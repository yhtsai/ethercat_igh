cmake_minimum_required(VERSION 2.8.3)
project(ethercat_igh)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED)

catkin_package(
#  CATKIN_DEPENDS hardware_interface roscpp
	DEPENDS ethercat
	INCLUDE_DIRS include
	LIBRARIES ethercat_igh 
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

## Declare a cpp library
add_library(ethercat_igh
  src/ethercat_igh.c
)

## Specify libraries to link a library or executable target against
target_link_libraries(ethercat_igh ethercat ${catkin_LIBRARIES})

install(TARGETS ethercat_igh 
        ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
        LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
        RUNTIME DESTINATION ${CATKIN_GLOBAL_BIN_DESTINATION})

install(DIRECTORY include/${PROJECT_NAME}/
	DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
	FILES_MATCHING PATTERN "*.h"
)
