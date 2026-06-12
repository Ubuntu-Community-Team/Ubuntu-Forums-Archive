---
title: "Help installing Mesa drivers"
date: 2008-11-11
forum: General Help
---

### Post by Sydius on 2008-11-11
Due to a bug in the Ubuntu 8.10 mesa drivers, I want to revert to an older version.  I verified the software rendering version of 6.5 works fine (no bug), but it's very slow.  What version was in Ubuntu 8.04?

I downloaded the source for Mesa 6.5 and it makes/installs fine, per the instructions, when I do software rendering.  When I try the linux-dri-x86, though, I get this:

```

make[1]: Entering directory `/home/chris/installed/Mesa-6.5.3/src'
Making sources for linux-dri
make[2]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/glx/x11'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/glx/x11'
make[2]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa'
make[3]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa'
make[4]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/x86'
make[4]: Nothing to be done for `default'.
make[4]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/x86'
make[4]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/x86-64'
make[4]: Nothing to be done for `default'.
make[4]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/x86-64'
cd drivers/dri ; make
make[4]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri'
echo i810 i915tex i915 i965 mach64 mga r128 r200 r300 radeon s3v savage sis tdfx trident unichrome ffb nouveau
i810 i915tex i915 i965 mach64 mga r128 r200 r300 radeon s3v savage sis tdfx trident unichrome ffb nouveau
i810
make[5]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri/i810'
make[5]: Nothing to be done for `default'.
make[5]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri/i810'
i915tex
make[5]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri/i915tex'
gcc -c -I. -I../../../../../src/mesa/drivers/dri/common -Iserver -I../../../../../include -I../../../../../include/GL/internal -I../../../../../src/mesa -I../../../../../src/mesa/main -I../../../../../src/mesa/glapi -I../../../../../src/mesa/math -I../../../../../src/mesa/transform -I../../../../../src/mesa/shader -I../../../../../src/mesa/swrast -I../../../../../src/mesa/swrast_setup -I../../../../../src/egl/main -I../../../../../src/egl/drivers/dri `pkg-config --cflags libdrm`  -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -I../intel -DDRM_VBLANK_FLIP=DRM_VBLANK_FLIP ../common/dri_bufmgr.c -o ../common/dri_bufmgr.o
In file included from ../common/dri_bufmgr.c:37:
../common/dri_bufmgr.h:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../common/dri_bufmgr.h:83: error: expected declaration specifiers or ‘...’ before ‘drmBOList’
../common/dri_bufmgr.h:84: error: expected ‘)’ before ‘*’ token
../common/dri_bufmgr.h:85: error: expected ‘)’ before ‘*’ token
../common/dri_bufmgr.h:87: error: expected declaration specifiers or ‘...’ before ‘drmBOList’
In file included from ../common/dri_bufmgr.c:40:
../common/dri_bufpool.h:52: error: expected specifier-qualifier-list before ‘drmBO’
../common/dri_bufmgr.c:57: error: expected specifier-qualifier-list before ‘drmFence’
../common/dri_bufmgr.c: In function ‘driFenceBuffers’:
../common/dri_bufmgr.c:102: warning: implicit declaration of function ‘drmFenceBuffers’
../common/dri_bufmgr.c:102: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: In function ‘driFenceType’:
../common/dri_bufmgr.c:118: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: In function ‘driFenceUnReference’:
../common/dri_bufmgr.c:142: warning: implicit declaration of function ‘drmFenceDestroy’
../common/dri_bufmgr.c:142: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: In function ‘driFenceFinish’:
../common/dri_bufmgr.c:152: error: ‘DRM_FENCE_FLAG_WAIT_LAZY’ undeclared (first use in this function)
../common/dri_bufmgr.c:152: error: (Each undeclared identifier is reported only once
../common/dri_bufmgr.c:152: error: for each function it appears in.)
../common/dri_bufmgr.c:155: warning: implicit declaration of function ‘drmFenceWait’
../common/dri_bufmgr.c:155: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: In function ‘driFenceSignaled’:
../common/dri_bufmgr.c:170: warning: implicit declaration of function ‘drmFenceSignaled’
../common/dri_bufmgr.c:170: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: At top level:
../common/dri_bufmgr.c:177: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../common/dri_bufmgr.c: In function ‘driBOWaitIdle’:
../common/dri_bufmgr.c:202: error: ‘DriBufferPool’ has no member named ‘waitIdle’
../common/dri_bufmgr.c: In function ‘driBOData’:
../common/dri_bufmgr.c:296: error: ‘DRM_BO_FLAG_WRITE’ undeclared (first use in this function)
../common/dri_bufmgr.c:297: error: ‘DRM_BO_HINT_DONT_BLOCK’ undeclared (first use in this function)
../common/dri_bufmgr.c:304: error: ‘DRM_BO_HINT_DONT_FENCE’ undeclared (first use in this function)
../common/dri_bufmgr.c: In function ‘driBOSubData’:
../common/dri_bufmgr.c:328: error: ‘DRM_BO_FLAG_WRITE’ undeclared (first use in this function)
../common/dri_bufmgr.c: In function ‘driBOGetSubData’:
../common/dri_bufmgr.c:344: error: ‘DRM_BO_FLAG_READ’ undeclared (first use in this function)
../common/dri_bufmgr.c: In function ‘driBOSetStatic’:
../common/dri_bufmgr.c:363: error: ‘DriBufferPool’ has no member named ‘setstatic’
../common/dri_bufmgr.c:372: error: ‘DriBufferPool’ has no member named ‘setstatic’
../common/dri_bufmgr.c: In function ‘driGenBuffers’:
../common/dri_bufmgr.c:394: error: ‘DRM_BO_FLAG_MEM_TT’ undeclared (first use in this function)
../common/dri_bufmgr.c:394: error: ‘DRM_BO_FLAG_MEM_VRAM’ undeclared (first use in this function)
../common/dri_bufmgr.c:395: error: ‘DRM_BO_FLAG_MEM_LOCAL’ undeclared (first use in this function)
../common/dri_bufmgr.c:395: error: ‘DRM_BO_FLAG_READ’ undeclared (first use in this function)
../common/dri_bufmgr.c:395: error: ‘DRM_BO_FLAG_WRITE’ undeclared (first use in this function)
../common/dri_bufmgr.c: At top level:
../common/dri_bufmgr.c:437: error: expected declaration specifiers or ‘...’ before ‘drmBOList’
../common/dri_bufmgr.c: In function ‘driBOCreateList’:
../common/dri_bufmgr.c:440: warning: implicit declaration of function ‘drmBOCreateList’
../common/dri_bufmgr.c:440: error: ‘list’ undeclared (first use in this function)
../common/dri_bufmgr.c: At top level:
../common/dri_bufmgr.c:445: error: expected ‘)’ before ‘*’ token
../common/dri_bufmgr.c:453: error: expected ‘)’ before ‘*’ token
../common/dri_bufmgr.c:487: error: expected declaration specifiers or ‘...’ before ‘drmBOList’
../common/dri_bufmgr.c: In function ‘driBOValidateList’:
../common/dri_bufmgr.c:490: warning: implicit declaration of function ‘drmBOValidateList’
../common/dri_bufmgr.c:490: error: ‘list’ undeclared (first use in this function)
../common/dri_bufmgr.c: In function ‘driPoolTakeDown’:
../common/dri_bufmgr.c:497: error: ‘struct _DriBufferPool’ has no member named ‘takeDown’
make[5]: *** [../common/dri_bufmgr.o] Error 1
make[5]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri/i915tex'
make[4]: *** [subdirs] Error 1
make[4]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri'
make[3]: *** [linux-solo] Error 2
make[3]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src'
make: *** [default] Error 1
chris@chris-work-laptop:~/installed/Mesa-6.5.3$ locate drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/i810_drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/i830_drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/i915_drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/mga_drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/r128_drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/radeon_drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/savage_drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/sis_drm.h
/usr/src/linux-headers-2.6.27-7/include/drm/via_drm.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/drm.h


```

Any help?

---

### Post by Crafty Kisses on 2008-11-12
Try running these commands:
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
```
Then once you have ran those try to recompile it.

---

### Post by Sydius on 2008-11-12
I tried what you suggested.  I already had the newest version of linux-restricted-modules-generic and it said restricted-manager was provided by jockey-gtk, so I installed that.  I still get:

```
make[1]: Entering directory `/home/chris/installed/Mesa-6.5.3/src'
Making sources for linux-dri
make[2]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/glx/x11'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/glx/x11'
make[2]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa'
make[3]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa'
make[4]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/x86'
make[4]: Nothing to be done for `default'.
make[4]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/x86'
make[4]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/x86-64'
make[4]: Nothing to be done for `default'.
make[4]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/x86-64'
cd drivers/dri ; make
make[4]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri'
echo i810 i915tex i915 i965 mach64 mga r128 r200 r300 radeon s3v savage sis tdfx trident unichrome ffb nouveau
i810 i915tex i915 i965 mach64 mga r128 r200 r300 radeon s3v savage sis tdfx trident unichrome ffb nouveau
i810
make[5]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri/i810'
make[5]: Nothing to be done for `default'.
make[5]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri/i810'
i915tex
make[5]: Entering directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri/i915tex'
gcc -c -I. -I../../../../../src/mesa/drivers/dri/common -Iserver -I../../../../../include -I../../../../../include/GL/internal -I../../../../../src/mesa -I../../../../../src/mesa/main -I../../../../../src/mesa/glapi -I../../../../../src/mesa/math -I../../../../../src/mesa/transform -I../../../../../src/mesa/shader -I../../../../../src/mesa/swrast -I../../../../../src/mesa/swrast_setup -I../../../../../src/egl/main -I../../../../../src/egl/drivers/dri `pkg-config --cflags libdrm`  -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -I../intel -DDRM_VBLANK_FLIP=DRM_VBLANK_FLIP ../common/dri_bufmgr.c -o ../common/dri_bufmgr.o
In file included from ../common/dri_bufmgr.c:37:
../common/dri_bufmgr.h:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../common/dri_bufmgr.h:83: error: expected declaration specifiers or ‘...’ before ‘drmBOList’
../common/dri_bufmgr.h:84: error: expected ‘)’ before ‘*’ token
../common/dri_bufmgr.h:85: error: expected ‘)’ before ‘*’ token
../common/dri_bufmgr.h:87: error: expected declaration specifiers or ‘...’ before ‘drmBOList’
In file included from ../common/dri_bufmgr.c:40:
../common/dri_bufpool.h:52: error: expected specifier-qualifier-list before ‘drmBO’
../common/dri_bufmgr.c:57: error: expected specifier-qualifier-list before ‘drmFence’
../common/dri_bufmgr.c: In function ‘driFenceBuffers’:
../common/dri_bufmgr.c:102: warning: implicit declaration of function ‘drmFenceBuffers’
../common/dri_bufmgr.c:102: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: In function ‘driFenceType’:
../common/dri_bufmgr.c:118: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: In function ‘driFenceUnReference’:
../common/dri_bufmgr.c:142: warning: implicit declaration of function ‘drmFenceDestroy’
../common/dri_bufmgr.c:142: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: In function ‘driFenceFinish’:
../common/dri_bufmgr.c:152: error: ‘DRM_FENCE_FLAG_WAIT_LAZY’ undeclared (first use in this function)
../common/dri_bufmgr.c:152: error: (Each undeclared identifier is reported only once
../common/dri_bufmgr.c:152: error: for each function it appears in.)
../common/dri_bufmgr.c:155: warning: implicit declaration of function ‘drmFenceWait’
../common/dri_bufmgr.c:155: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: In function ‘driFenceSignaled’:
../common/dri_bufmgr.c:170: warning: implicit declaration of function ‘drmFenceSignaled’
../common/dri_bufmgr.c:170: error: ‘DriFenceObject’ has no member named ‘fence’
../common/dri_bufmgr.c: At top level:
../common/dri_bufmgr.c:177: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../common/dri_bufmgr.c: In function ‘driBOWaitIdle’:
../common/dri_bufmgr.c:202: error: ‘DriBufferPool’ has no member named ‘waitIdle’
../common/dri_bufmgr.c: In function ‘driBOData’:
../common/dri_bufmgr.c:296: error: ‘DRM_BO_FLAG_WRITE’ undeclared (first use in this function)
../common/dri_bufmgr.c:297: error: ‘DRM_BO_HINT_DONT_BLOCK’ undeclared (first use in this function)
../common/dri_bufmgr.c:304: error: ‘DRM_BO_HINT_DONT_FENCE’ undeclared (first use in this function)
../common/dri_bufmgr.c: In function ‘driBOSubData’:
../common/dri_bufmgr.c:328: error: ‘DRM_BO_FLAG_WRITE’ undeclared (first use in this function)
../common/dri_bufmgr.c: In function ‘driBOGetSubData’:
../common/dri_bufmgr.c:344: error: ‘DRM_BO_FLAG_READ’ undeclared (first use in this function)
../common/dri_bufmgr.c: In function ‘driBOSetStatic’:
../common/dri_bufmgr.c:363: error: ‘DriBufferPool’ has no member named ‘setstatic’
../common/dri_bufmgr.c:372: error: ‘DriBufferPool’ has no member named ‘setstatic’
../common/dri_bufmgr.c: In function ‘driGenBuffers’:
../common/dri_bufmgr.c:394: error: ‘DRM_BO_FLAG_MEM_TT’ undeclared (first use in this function)
../common/dri_bufmgr.c:394: error: ‘DRM_BO_FLAG_MEM_VRAM’ undeclared (first use in this function)
../common/dri_bufmgr.c:395: error: ‘DRM_BO_FLAG_MEM_LOCAL’ undeclared (first use in this function)
../common/dri_bufmgr.c:395: error: ‘DRM_BO_FLAG_READ’ undeclared (first use in this function)
../common/dri_bufmgr.c:395: error: ‘DRM_BO_FLAG_WRITE’ undeclared (first use in this function)
../common/dri_bufmgr.c: At top level:
../common/dri_bufmgr.c:437: error: expected declaration specifiers or ‘...’ before ‘drmBOList’
../common/dri_bufmgr.c: In function ‘driBOCreateList’:
../common/dri_bufmgr.c:440: warning: implicit declaration of function ‘drmBOCreateList’
../common/dri_bufmgr.c:440: error: ‘list’ undeclared (first use in this function)
../common/dri_bufmgr.c: At top level:
../common/dri_bufmgr.c:445: error: expected ‘)’ before ‘*’ token
../common/dri_bufmgr.c:453: error: expected ‘)’ before ‘*’ token
../common/dri_bufmgr.c:487: error: expected declaration specifiers or ‘...’ before ‘drmBOList’
../common/dri_bufmgr.c: In function ‘driBOValidateList’:
../common/dri_bufmgr.c:490: warning: implicit declaration of function ‘drmBOValidateList’
../common/dri_bufmgr.c:490: error: ‘list’ undeclared (first use in this function)
../common/dri_bufmgr.c: In function ‘driPoolTakeDown’:
../common/dri_bufmgr.c:497: error: ‘struct _DriBufferPool’ has no member named ‘takeDown’
make[5]: *** [../common/dri_bufmgr.o] Error 1
make[5]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri/i915tex'
make[4]: *** [subdirs] Error 1
make[4]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa/drivers/dri'
make[3]: *** [linux-solo] Error 2
make[3]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src/mesa'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/chris/installed/Mesa-6.5.3/src'
make: *** [default] Error 1
```

---

