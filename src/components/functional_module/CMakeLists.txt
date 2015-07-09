include_directories (
  ./include/
  ../include/
  ../application_manager/include
  ../connection_handler/include/
  ../utils/include
  ../config_profile/include
  ${JSONCPP_INCLUDE_DIRECTORY}
  ${LOG4CXX_INCLUDE_DIRECTORY}
  ${CMAKE_BINARY_DIR}/src/components/
)

set (SOURCES
    ./src/generic_module.cc
    ./src/plugin_manager.cc
    ./src/settings.cc
)

add_library("FunctionalModule" ${SOURCES})

if(ENABLE_LOG)
  target_link_libraries("FunctionalModule" log4cxx -L${LOG4CXX_LIBS_DIRECTORY})
endif()

if(BUILD_TESTS)
  add_subdirectory(test)
endif()