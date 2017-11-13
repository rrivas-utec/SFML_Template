cmake_minimum_required(VERSION 3.8)

set(CMAKE_PROJECT_NAME "UTEC_CS1100_Project")
project(${CMAKE_PROJECT_NAME})

set(CMAKE_CXX_STANDARD 14)

set(SFML_ROOT "C:/SFML-2.4.2")
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${SFML_ROOT}/cmake/modules")
set(CMAKE_PREFIX_PATH ${CMAKE_PREFIX_PATH} "${SFML_ROOT}/lib")
set(SFML_INCLUDE_DIR "${SFML_ROOT}/include")

set(SOURCE_FILES main.cpp)
add_executable(${CMAKE_PROJECT_NAME} ${SOURCE_FILES})

set(SFML_STATIC_LIBRARIES TRUE)
find_package(SFML COMPONENTS audio network graphics window system REQUIRED)

# Detect and add SFML
if(SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    target_link_libraries(${CMAKE_PROJECT_NAME} ${SFML_LIBRARIES} ${SFML_DEPENDENCIES})
endif()
