#
#
# Copyright (c) 1991-2020 by the GMT Team (https://www.generic-mapping-tools.org/team.html)
# See LICENSE.TXT file for copying and redistribution conditions.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; version 3 or any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Lesser General Public License for more details.
#
# Contact info: www.generic-mapping-tools.org
#-------------------------------------------------------------------------------
#
# To modify the cmake process, edit your cmake/ConfigUser.cmake and cmake/ConfigUserAdvanced.cmake files
#

set (SUPPL_NAME gshhg)

# source files
set (SUPPL_HEADERS gshhg.h gmt_gshhg.h)
set (SUPPL_PROGS_SRCS gshhg.c)

# example files
set (SUPPL_EXAMPLE_FILES README.gshhg)

# lib sources
set (LIB_SRCS ${SUPPL_PROGS_SRCS})

# create build targets
string (REPLACE ".c" "" _gmt_modules "${SUPPL_PROGS_SRCS}")
install_module_symlink (${_gmt_modules})

# install example data
install (FILES ${SUPPL_EXAMPLE_FILES}
	DESTINATION ${GMT_DOCDIR}/supplements/${SUPPL_NAME}
	COMPONENT Documentation)

# install headers
if (BUILD_DEVELOPER)
	install (FILES ${SUPPL_HEADERS}
		DESTINATION ${GMT_INCLUDEDIR}/${SUPPL_NAME}
		COMPONENT Runtime)
endif (BUILD_DEVELOPER)
