cmake_minimum_required(VERSION 3.26)
project(ejercicios3,4y5)

set(CMAKE_CXX_STANDARD 17)

add_library(matematicas STATIC matematicas.cpp)

add_library(matematicas_shared SHARED matematicas.cpp)

add_executable(main main.cpp funciones.cpp funciones.h)
add_executable(funciones funciones.cpp funciones.h
        funciones.cpp
        funciones.h
        matematicas.cpp)

target_link_libraries(main PRIVATE matematicas)

target_link_libraries(main PRIVATE fmt::fmt)

include(FetchContent)
FetchContent_Declare(
        fmt
        GIT_REPOSITORY https://github.com/fmtlib/fmt.git
        GIT_TAG        7.1.3
)

FetchContent_MakeAvailable(fmt)
