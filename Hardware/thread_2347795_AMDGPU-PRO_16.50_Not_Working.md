---
title: "AMDGPU-PRO 16.50 Not Working"
date: 2016-12-28
forum: Hardware
---

### Post by Joker5bb on 2016-12-28
I have installed the AMDGPU-PRO 16.50 driver by following the instructions from the provided link below

[http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)

It does not seem to load properly

$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

I have kernel 4.4. DKMS build fails on kernel 4.6.4 and higher.
Whats the appropriate kernel to run this on and how can I troubleshoot?

---

### Post by QIII on 2016-12-28
Hello!

What model of GPU do you have?

Support for kernel 4.4 is experimental.  I had to go to 4.8 on 16.04 to get things to work properly with an R9 380X.

16.10 was as simple as installing from the repo.

---

### Post by Joker5bb on 2016-12-28
I have the R9 290X. I am going to try the 4.8 kernel now

---

### Post by QIII on 2016-12-28
The 290X *may* work, but it's not guaranteed.  It's a GCN 1.1 GPU.  GCN 1.2 are fully supported, and AMD is working backwards to cover earler GCN cards. Kernel 4.9 is supposed to work the kinks out of GCN 1.1.

---

### Post by Joker5bb on 2016-12-28
ERROR (dkms apport): kernel package linux-headers-4.8.0-040800-generic is not supported
Error! Bad return status for module build on kernel: 4.8.0-040800-generic (x86_64)
Consult /var/lib/dkms/amdgpu-pro/16.50-362463/build/make.log for more information.

$ cat /var/lib/dkms/amdgpu-pro/16.50-362463/build/make.logDKMS make.log for amdgpu-pro-16.50-362463 for kernel 4.8.0-040800-generic (x86_64)
Wed Dec 28 20:18:38 EST 2016
make: Entering directory '/usr/src/linux-headers-4.8.0-040800-generic'
  LD      /var/lib/dkms/amdgpu-pro/16.50-362463/build/built-in.o
  LD      /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/built-in.o
  CC [M]  /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/amdgpu_drv.o
In file included from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/backport.h:5:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/include/kcl/kcl_ttm.h: In function \u2018kcl_ttm_bo_reserve\u2019:
/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/include/kcl/kcl_ttm.h:116:9: error: too many arguments to function \u2018ttm_bo_reserve\u2019
  return ttm_bo_reserve(bo, interruptible, no_wait, false, ticket);
         ^
In file included from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/include/kcl/kcl_ttm.h:6:0,
                 from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/backport.h:5,
                 from <command-line>:0:
./include/drm/ttm/ttm_bo_driver.h:863:19: note: declared here
 static inline int ttm_bo_reserve(struct ttm_buffer_object *bo,
                   ^
In file included from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/backport.h:5:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/include/kcl/kcl_ttm.h: In function \u2018kcl_ttm_bo_move_accel_cleanup\u2019:
/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/include/kcl/kcl_ttm.h:153:11: error: incompatible type for argument 4 of \u2018ttm_bo_move_accel_cleanup\u2019
    evict, no_wait_gpu, new_mem);
           ^
In file included from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/include/kcl/kcl_ttm.h:6:0,
                 from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/backport.h:5,
                 from <command-line>:0:
./include/drm/ttm/ttm_bo_driver.h:1032:12: note: expected \u2018struct ttm_mem_reg *\u2019 but argument is of type \u2018bool {aka _Bool}\u2019
 extern int ttm_bo_move_accel_cleanup(struct ttm_buffer_object *bo,
            ^
In file included from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/backport.h:5:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/include/kcl/kcl_ttm.h:152:9: error: too many arguments to function \u2018ttm_bo_move_accel_cleanup\u2019
  return ttm_bo_move_accel_cleanup(bo, fence,
         ^
In file included from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/include/kcl/kcl_ttm.h:6:0,
                 from /var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/../backport/backport.h:5,
                 from <command-line>:0:
./include/drm/ttm/ttm_bo_driver.h:1032:12: note: declared here
 extern int ttm_bo_move_accel_cleanup(struct ttm_buffer_object *bo,
            ^
scripts/Makefile.build:289: recipe for target '/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/amdgpu_drv.o' failed
make[2]: *** [/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu/amdgpu_drv.o] Error 1
scripts/Makefile.build:440: recipe for target '/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu' failed
make[1]: *** [/var/lib/dkms/amdgpu-pro/16.50-362463/build/amd/amdgpu] Error 2
Makefile:1477: recipe for target '_module_/var/lib/dkms/amdgpu-pro/16.50-362463/build' failed
make: *** [_module_/var/lib/dkms/amdgpu-pro/16.50-362463/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.8.0-040800-generic'

---

