
if (WIN32)
   set(VCOS_PLATFORM win32)
else ()
   set(VCOS_PLATFORM pthreads)
   add_definitions(-Wall -Werror -Wno-error=parentheses-equality -Wno-error=enum-conversion)
endif ()

include_directories( ../../../..
                     ../../../../interface/vcos/${VCOS_PLATFORM}
                     ../../../../host_applications/linux/kernel_headers )

add_library(vcsm ${SHARED} user-vcsm.c)

target_link_libraries(vcsm vcos)

install(TARGETS vcsm DESTINATION lib)

