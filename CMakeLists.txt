cmake_minimum_required(VERSION 2.8)
 
project(BilateralImageFilter)
ENABLE_TESTING()
 
find_package(ITK REQUIRED)
include(${ITK_USE_FILE})

# set(COMMON_INCLUDES ${PROJECT_SOURCE_DIR}/include)
set(PROJECT_LIB_NAME ${PROJECT_NAME_STR}_impl)
# include_directories(${COMMON_INCLUDES})
file(GLOB SRC_FILES ${PROJECT_SOURCE_DIR}/src/*.cxx)

# add_library(${PROJECT_LIB_NAME} ${SRC_FILES})
# target_link_libraries(${PROJECT_LIB_NAME} ${ITK_LIBRARIES})
add_executable(BilateralImageFilter ${SRC_FILES})
target_link_libraries(BilateralImageFilter ${ITK_LIBRARIES})

add_test(TestBilateralFilter BilateralImageFilter ${PROJECT_SOURCE_DIR}/data/Gourds.png Gourds_out.png 2 2)