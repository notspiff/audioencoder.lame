project(lame)

cmake_minimum_required(VERSION 2.8)

include(ExternalProject)
externalproject_add(lame
                    SOURCE_DIR ${CMAKE_SOURCE_DIR}
                    CONFIGURE_COMMAND <SOURCE_DIR>/configure 
                      --prefix=${OUTPUT_DIR}
                      --disable-gtktest
                      --disable-frontend
                      --disable-decoder
                    BUILD_COMMAND make -C libmp3lame
                    INSTALL_COMMAND ""
                    BUILD_IN_SOURCE 1)
                  
install(CODE "execute_process(COMMAND make -C include install WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})")
install(CODE "execute_process(COMMAND make -C libmp3lame install WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})")
