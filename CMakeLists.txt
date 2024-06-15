cmake_minimum_required(VERSION 3.0.0)
project(ati_sensor)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

find_package(LibXml2 REQUIRED)

add_library(ati_sensor src/ft_sensor.cpp)
target_include_directories(ati_sensor PUBLIC "include" ${LIBXML2_INCLUDE_DIR})
target_link_libraries(ati_sensor ${LIBXML2_LIBRARIES})

add_executable(simple_reader_test test/simple_reader.cpp)
target_link_libraries(simple_reader_test ati_sensor)

add_executable(gauge_bias_tester  test/test_gauge_bias.cpp)
target_link_libraries(gauge_bias_tester ati_sensor)
