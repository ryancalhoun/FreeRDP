# FreeRDP: A Remote Desktop Protocol Implementation
# FreeRDP cmake build script
#
# Copyright 2012 Marc-Andre Moreau <marcandre.moreau@gmail.com>
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

set(MODULE_NAME "sample")
set(MODULE_PREFIX "CHANNEL_SAMPLE_CLIENT")

set(${MODULE_PREFIX}_SRCS
	skel_main.c
	skel_main.h)

add_library(${MODULE_NAME} ${${MODULE_PREFIX}_SRCS})
set_target_properties(${MODULE_NAME} PROPERTIES PREFIX "")

if(MONOLITHIC_BUILD)
	target_link_libraries(${MODULE_NAME} freerdp)
else()
	target_link_libraries(${MODULE_NAME} freerdp-utils)
endif()

install(TARGETS ${MODULE_NAME} DESTINATION ${FREERDP_PLUGIN_PATH})