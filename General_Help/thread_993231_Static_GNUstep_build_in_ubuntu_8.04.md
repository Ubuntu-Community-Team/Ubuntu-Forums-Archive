---
title: "Static GNUstep build in ubuntu 8.04"
date: 2008-11-25
forum: General Help
---

### Post by dhusubali on 2008-11-25
Hello,
I am trying a static build of GNUstep libraries in ubuntu.  I was successful until GNUstep/core/base library. When trying to compile gui library I got problem while linking. While linking somehow it does not recognize the tiff library. But I see that both libtiff.a and libtiff.so.4.2.1 are in /usr/lib/. 
Any help would be appreciated. Thanks in advance.

The specific error message I get is:
usr/GNUstep/System/Library/Libraries/libgnustep-base.a(objc-load.m.o): In function `__objc_dynamic_link':
/home/khatun/modules/core/base/Source/dynamic-load.h:65: warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
..
..
..
..
..
..
..

/usr/GNUstep/System/Library/Libraries/libgnustep-base.a(GSFileHandle.m.o): In function `getAddr':
/home/khatun/modules/core/base/Source/GSFileHandle.m:202: warning: Using 'getservbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffOpenDataRead':
/home/khatun/modules/core/gui/Source/tiff.m:200: undefined reference to `TIFFSetErrorHandler'
/home/khatun/modules/core/gui/Source/tiff.m:201: undefined reference to `TIFFSetWarningHandler'
/home/khatun/modules/core/gui/Source/tiff.m:211: undefined reference to `TIFFClientOpen'
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffOpenDataWrite':
/home/khatun/modules/core/gui/Source/tiff.m:230: undefined reference to `TIFFClientOpen'
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffClose':
/home/khatun/modules/core/gui/Source/tiff.m:241: undefined reference to `TIFFClose'
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffGetImageCount':
/home/khatun/modules/core/gui/Source/tiff.m:253: undefined reference to `TIFFReadDirectory'
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffGetInfo':
/home/khatun/modules/core/gui/Source/tiff.m:275: undefined reference to `TIFFSetDirectory'
/home/khatun/modules/core/gui/Source/tiff.m:280: undefined reference to `TIFFGetField'
/home/khatun/modules/core/gui/Source/tiff.m:281: undefined reference to `TIFFGetField'
/home/khatun/modules/core/gui/Source/tiff.m:282: undefined reference to `TIFFGetField'
/home/khatun/modules/core/gui/Source/tiff.m:284: undefined reference to `TIFFGetField'
/home/khatun/modules/core/gui/Source/tiff.m:285: undefined reference to `TIFFGetField'
../Source/./obj/libgnustep-gui.a(tiff.m.o):/home/khatun/modules/core/gui/Source/tiff.m:286: more undefined references to `TIFFGetField' follow
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffGetInfo':
/home/khatun/modules/core/gui/Source/tiff.m:294: undefined reference to `TIFFGetFieldDefaulted'
/home/khatun/modules/core/gui/Source/tiff.m:295: undefined reference to `TIFFGetFieldDefaulted'
/home/khatun/modules/core/gui/Source/tiff.m:297: undefined reference to `TIFFGetFieldDefaulted'
/home/khatun/modules/core/gui/Source/tiff.m:302: undefined reference to `TIFFGetField'
/home/khatun/modules/core/gui/Source/tiff.m:313: undefined reference to `TIFFFileName'
/home/khatun/modules/core/gui/Source/tiff.m:313: undefined reference to `TIFFError'
/home/khatun/modules/core/gui/Source/tiff.m:317: undefined reference to `TIFFFileName'
/home/khatun/modules/core/gui/Source/tiff.m:317: undefined reference to `TIFFError'
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffRead':
/home/khatun/modules/core/gui/Source/tiff.m:363: undefined reference to `TIFFScanlineSize'
/home/khatun/modules/core/gui/Source/tiff.m:364: undefined reference to `_TIFFmalloc'
/home/khatun/modules/core/gui/Source/tiff.m:376: undefined reference to `TIFFReadScanline'
/home/khatun/modules/core/gui/Source/tiff.m:386: undefined reference to `TIFFReadScanline'
/home/khatun/modules/core/gui/Source/tiff.m:397: undefined reference to `TIFFReadScanline'
/home/khatun/modules/core/gui/Source/tiff.m:415: undefined reference to `TIFFReadScanline'
/home/khatun/modules/core/gui/Source/tiff.m:425: undefined reference to `TIFFReadScanline'
/home/khatun/modules/core/gui/Source/tiff.m:437: undefined reference to `_TIFFfree'
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffWrite':
/home/khatun/modules/core/gui/Source/tiff.m:456: undefined reference to `TIFFSetField'
/home/khatun/modules/core/gui/Source/tiff.m:457: undefined reference to `TIFFSetField'
/home/khatun/modules/core/gui/Source/tiff.m:458: undefined reference to `TIFFSetField'
/home/khatun/modules/core/gui/Source/tiff.m:460: undefined reference to `TIFFSetField'
/home/khatun/modules/core/gui/Source/tiff.m:461: undefined reference to `TIFFSetField'
../Source/./obj/libgnustep-gui.a(tiff.m.o):/home/khatun/modules/core/gui/Source/tiff.m:462: more undefined references to `TIFFSetField' follow
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffWrite':
/home/khatun/modules/core/gui/Source/tiff.m:483: undefined reference to `TIFFWriteScanline'
/home/khatun/modules/core/gui/Source/tiff.m:495: undefined reference to `TIFFWriteScanline'
/home/khatun/modules/core/gui/Source/tiff.m:507: undefined reference to `TIFFWriteScanline'
/home/khatun/modules/core/gui/Source/tiff.m:517: undefined reference to `TIFFWriteScanline'
/home/khatun/modules/core/gui/Source/tiff.m:525: undefined reference to `TIFFFileName'
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffGetColormap':
/home/khatun/modules/core/gui/Source/tiff.m:576: undefined reference to `TIFFGetField'
/home/khatun/modules/core/gui/Source/tiff.m:579: undefined reference to `TIFFFileName'
/home/khatun/modules/core/gui/Source/tiff.m:579: undefined reference to `TIFFError'
/home/khatun/modules/core/gui/Source/tiff.m:584: undefined reference to `TIFFFileName'
/home/khatun/modules/core/gui/Source/tiff.m:584: undefined reference to `TIFFWarning'
../Source/./obj/libgnustep-gui.a(tiff.m.o): In function `NSTiffIsCodecConfigured':
/home/khatun/modules/core/gui/Source/tiff.m:594: undefined reference to `TIFFIsCODECConfigured'
collect2: ld returned 1 exit status
make[2]: *** [obj/set_show_service] Error 1
make[1]: *** [set_show_service.all.tool.variables] Error 2
make: *** [internal-all] Error 2

---

