cmake_minimum_required(VERSION 3.0.0)
project(test VERSION 0.1.0)

set(LINK_DIR /usr/local/lib)
set(INC_DIR /usr/local/include)  

include(CTest)
enable_testing()


include_directories(${INC_DIR})
link_directories(${LINK_DIR})

#链接 avutil
add_library(lavutil SHARED IMPORTED)
set_property(TARGET lavutil 
PROPERTY IMPORTED_LOCATION 
${LINK_DIR}/libavutil.dylib)
#链接 avformat
add_library(avformat SHARED IMPORTED)
set_property(TARGET avformat 
PROPERTY IMPORTED_LOCATION 
${LINK_DIR}/libavformat.dylib)
#链接 avcodec
add_library(avcodec SHARED IMPORTED)
set_property(TARGET avcodec 
PROPERTY IMPORTED_LOCATION 
${LINK_DIR}/libavcodec.dylib)
#链接 avdevice
add_library(avdevice SHARED IMPORTED)
set_property(TARGET avdevice 
PROPERTY IMPORTED_LOCATION 
${LINK_DIR}/libavdevice.dylib)

#链接 avfilter
add_library(avfilter SHARED IMPORTED)
set_property(TARGET avfilter 
PROPERTY IMPORTED_LOCATION 
${LINK_DIR}/libavfilter.dylib)

#链接 swresample
add_library(swresample SHARED IMPORTED)
set_property(TARGET swresample 
PROPERTY IMPORTED_LOCATION 
${LINK_DIR}/libswresample.dylib)

#链接 swscale
add_library(swscale SHARED IMPORTED)
set_property(TARGET swscale 
PROPERTY IMPORTED_LOCATION 
${LINK_DIR}/libswscale.dylib)



add_executable(myFFmpegProject main.cpp)

target_link_libraries(
    myFFmpegProject
    lavutil
    avformat
    avcodec
    avdevice
    avfilter
    swresample
    swscale
)
set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
