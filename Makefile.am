ACLOCAL_AMFLAGS = -I m4

if ENABLE_RUNTIME_LINKING
AM_CPPFLAGS = -DENABLE_RUNTIME_LINKING
endif

if ENABLE_TOOLS
bin_PROGRAMS = s2tc_compress s2tc_decompress s2tc_from_s3tc
s2tc_from_s3tc_SOURCES = s2tc_from_s3tc.cpp s2tc_license.h
s2tc_compress_SOURCES = s2tc_compress.c txc_dxtn.h s2tc_license.h
s2tc_decompress_SOURCES = s2tc_decompress.c txc_dxtn.h s2tc_license.h
man1_MANS = s2tc_compress.1 s2tc_decompress.1 s2tc_from_s3tc.1
if ENABLE_RUNTIME_LINKING
s2tc_compress_LDADD = $(LIBDL_LDADD)
s2tc_decompress_LDADD = $(LIBDL_LDADD)
else
if ENABLE_LIB
s2tc_compress_LDADD = libtxc_dxtn.la
s2tc_decompress_LDADD = libtxc_dxtn.la
else
s2tc_compress_LDADD = -ltxc_dxtn
s2tc_decompress_LDADD = -ltxc_dxtn
endif
endif
endif

if ENABLE_LIB
lib_LTLIBRARIES = libtxc_dxtn.la
libtxc_dxtn_la_SOURCES = s2tc_algorithm.cpp s2tc_libtxc_dxtn.cpp s2tc_common.h s2tc_algorithm.h txc_dxtn.h s2tc_license.h
libtxc_dxtn_la_LDFLAGS = -avoid-version -nodefaultlibs
libtxc_dxtn_la_LIBADD = -lm
libtxc_dxtn_la_CFLAGS = -fvisibility=hidden -Wold-style-definition -Wstrict-prototypes -Wsign-compare -Wdeclaration-after-statement
library_includedir = $(includedir)
library_include_HEADERS = txc_dxtn.h
pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_HEADERS = txc_dxtn.pc
endif

EXTRA_DIST = README.txt autogen.sh
