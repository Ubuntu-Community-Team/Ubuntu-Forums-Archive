---
title: "ZOOM 3029 USB  dial up modem"
date: 2012-05-07
forum: Hardware
---

### Post by hermannelson on 2012-05-07
Hello,
I am stuck in the install if the Zoom dcg modem. It is unable to compile the module?



Any Help would be much appreciated and Thanks in advance.

Carl
d /lib/modules/3.2.0-24-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-24-generic/build" "M=/usr/lib/dgcmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.2.0-24-generic/build/.tmp_versions/dgcusbdcp.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.2.0-24-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-24-generic/build" "M=/usr/lib/dgcmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  CC [M]  /usr/lib/dgcmodem/modules/mod_dgcusbdcp.o
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c: In function 'dgcUsbWrite':
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c:173:2: warning: format '%d' expects argument of type 'int', but argument 5 has type 'size_t' [-Wformat]
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c: At top level:
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c:263:36: error: 'SPIN_LOCK_UNLOCKED' undeclared here (not in a function)
make[2]: *** [/usr/lib/dgcmodem/modules/mod_dgcusbdcp.o] Error 1
make[1]: *** [_module_/usr/lib/dgcmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [all] Error 2



+ gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.6/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5)

---

