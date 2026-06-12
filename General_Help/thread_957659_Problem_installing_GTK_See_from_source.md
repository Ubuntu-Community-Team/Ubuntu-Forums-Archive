---
title: "Problem installing GTK See from source"
date: 2008-10-24
forum: General Help
---

### Post by Ingo88 on 2008-10-24
Hi!

I tried to install [GTK See](http://gtksee.berlios.de/), but *make* didn't work.

Here's the output:
```
make  all-recursive
make[1]: Entering directory `/home/ingo/gtksee-0.6.0b-1'
Making all in intl
make[2]: Entering directory `/home/ingo/gtksee-0.6.0b-1/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ingo/gtksee-0.6.0b-1/intl'
Making all in po
make[2]: Entering directory `/home/ingo/gtksee-0.6.0b-1/po'
PATH=../src:$PATH : --default-domain=gtksee --directory=.. \
	  --add-comments --keyword=_ --keyword=N_ \
	  --files-from=./POTFILES.in \
	&& test ! -f gtksee.po \
	   || ( rm -f ./gtksee.pot \
		&& mv gtksee.po ./gtksee.pot )
file=./`echo zh_CN.EUC | sed 's,.*/,,'`.gmo \
	  && rm -f $file && PATH=../src:$PATH no -o $file zh_CN.EUC.po
/bin/sh: no: not found
make[2]: *** [zh_CN.EUC.gmo] Error 127
make[2]: Leaving directory `/home/ingo/gtksee-0.6.0b-1/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ingo/gtksee-0.6.0b-1'
make: *** [all] Error 2
```

There didn't seem to be any problem with the ./configure step:
```
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for POSIXized ISC... no
checking for a BSD compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking for ranlib... ranlib
checking for pow in -lm... yes
checking for gzread in -lz... yes
checking for jpeg_read_header in -ljpeg... yes
checking for TIFFGetVersion in -ltiff... yes
checking for png_read_info in -lpng... yes
checking how to run the C preprocessor... gcc -E
checking for os2.h... no
checking for ntohl in -lsocket... no
checking for gtk-config... gtk-config
checking for GTK - version >= 1.0.0... yes
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for unistd.h... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for getcwd... yes
checking for inline... inline
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... (cached) yes
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for argz.h... yes
checking for limits.h... yes
checking for locale.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getcwd... (cached) yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for stpcpy... yes
checking for LC_MESSAGES... yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for libintl.h... yes
checking for gettext in libc... yes
checking for msgfmt... no
checking whether catgets can be used... no
checking for msgfmt... (cached) no
checking for gmsgfmt... no
checking for xgettext... :
checking for catalogs to be installed...  zh_CN.EUC fr es de ru ru_UA pl
configure: creating ./config.status
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating Makefile
config.status: creating intl/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: linking ./intl/libgettext.h to intl/libintl.h

GTK See 0.6.0-Beta configure result:

JPEG format support: yes
TIFF format support: yes
PNG  format support: yes

GTK+ version: 1.2.10 (up-to-date)
===============================================================
Type "make" to compile gtksee.
```

I didn't find any Ubuntu packages anywhere. Or is there somewhere?

Thanks in advance for your help! :D

---

### Post by Ingo88 on 2008-12-31
Bump

---

