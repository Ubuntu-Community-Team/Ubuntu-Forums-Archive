---
title: "Radeon R9 290 Installation Problems"
date: 2018-02-18
forum: Hardware
---

### Post by Linux_cat on 2018-02-18
Hi all, im currently attepting to install the official driver on my 16.04 install:

```
Linux sarndeep-desktop 4.14.0-041400-generic #201711122031 SMP Sun Nov 12 20:32:29 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

but the install keeps failing with:




```
etting up amdgpu-pro-core (17.40-492261) ...
Setting up amdgpu-pro-dkms (17.40-492261) ...
Loading new amdgpu-17.40-492261 DKMS files...
First Installation: checking all kernels...
Building only for 4.14.0-041400-generic
Building for architecture x86_64
Building initial module for 4.14.0-041400-generic
ERROR (dkms apport): kernel package linux-headers-4.14.0-041400-generic is not supported
Error! Bad return status for module build on kernel: 4.14.0-041400-generic (x86_64)
Consult /var/lib/dkms/amdgpu/17.40-492261/build/make.log for more information.

```

The log file: 
```
DKMS make.log for amdgpu-17.40-492261 for kernel 4.14.0-041400-generic (x86_64)
Sun 18 Feb 09:00:15 GMT 2018
make: Entering directory '/usr/src/linux-headers-4.14.0-041400-generic'
  AR      /var/lib/dkms/amdgpu/17.40-492261/build/built-in.o
  AR      /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/built-in.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_module.o
  AR      /var/lib/dkms/amdgpu/17.40-492261/build/ttm/built-in.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_device.o
  AR      /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/built-in.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_chardev.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/ttm/ttm_memory.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/ttm/ttm_tt.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_topology.o
  AR      /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/built-in.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.o
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h: In function ‘kcl_drm_universal_plane_init’:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:271:29: error: incompatible type for argument 7 of ‘drm_universal_plane_init’
      formats, format_count, type, name);
                             ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: expected ‘const uint64_t * {aka const long long unsigned int *}’ but argument is of type ‘enum drm_plane_type’
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:271:35: error: incompatible type for argument 8 of ‘drm_universal_plane_init’
      formats, format_count, type, name);
                                   ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: expected ‘enum drm_plane_type’ but argument is of type ‘const char *’
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:270:10: error: too few arguments to function ‘drm_universal_plane_init’
   return drm_universal_plane_init(dev, plane, possible_crtcs, funcs,
          ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: declared here
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h: In function ‘kcl_drm_calc_vbltimestamp_from_scanoutpos’:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:332:9: error: too many arguments to function ‘drm_calc_vbltimestamp_from_scanoutpos’
  return drm_calc_vbltimestamp_from_scanoutpos(dev, pipe, max_error, vblank_time,
         ^
In file included from ./include/drm/drmP.h:83:0,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_vblank.h:173:6: note: declared here
 bool drm_calc_vbltimestamp_from_scanoutpos(struct drm_device *dev,
      ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h: In function ‘kcl_drm_universal_plane_init’:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:271:29: error: incompatible type for argument 7 of ‘drm_universal_plane_init’
      formats, format_count, type, name);
                             ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: expected ‘const uint64_t * {aka const long long unsigned int *}’ but argument is of type ‘enum drm_plane_type’
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:271:35: error: incompatible type for argument 8 of ‘drm_universal_plane_init’
      formats, format_count, type, name);
                                   ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: expected ‘enum drm_plane_type’ but argument is of type ‘const char *’
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:270:10: error: too few arguments to function ‘drm_universal_plane_init’
   return drm_universal_plane_init(dev, plane, possible_crtcs, funcs,
          ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: declared here
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h: In function ‘kcl_drm_calc_vbltimestamp_from_scanoutpos’:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:332:9: error: too many arguments to function ‘drm_calc_vbltimestamp_from_scanoutpos’
  return drm_calc_vbltimestamp_from_scanoutpos(dev, pipe, max_error, vblank_time,
         ^
In file included from ./include/drm/drmP.h:83:0,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/ttm/backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_vblank.h:173:6: note: declared here
 bool drm_calc_vbltimestamp_from_scanoutpos(struct drm_device *dev,
      ^
/var/lib/dkms/amdgpu/17.40-492261/build/ttm/ttm_tt.c: At top level:
/var/lib/dkms/amdgpu/17.40-492261/build/ttm/ttm_tt.c:43:30: fatal error: drm/drm_mem_util.h: No such file or directory
compilation terminated.
scripts/Makefile.build:314: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/ttm/ttm_tt.o' failed
make[2]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/ttm/ttm_tt.o] Error 1
make[2]: *** Waiting for unfinished jobs....
scripts/Makefile.build:314: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/ttm/ttm_memory.o' failed
make[2]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/ttm/ttm_memory.o] Error 1
scripts/Makefile.build:573: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/ttm' failed
make[1]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/ttm] Error 2
make[1]: *** Waiting for unfinished jobs....
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_pasid.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/main.o
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/../include/../backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h: In function ‘kcl_drm_universal_plane_init’:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:271:29: error: incompatible type for argument 7 of ‘drm_universal_plane_init’
      formats, format_count, type, name);
                             ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/../include/../backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: expected ‘const uint64_t * {aka const long long unsigned int *}’ but argument is of type ‘enum drm_plane_type’
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/../include/../backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:271:35: error: incompatible type for argument 8 of ‘drm_universal_plane_init’
      formats, format_count, type, name);
                                   ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/../include/../backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: expected ‘enum drm_plane_type’ but argument is of type ‘const char *’
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/../include/../backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:270:10: error: too few arguments to function ‘drm_universal_plane_init’
   return drm_universal_plane_init(dev, plane, possible_crtcs, funcs,
          ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/../include/../backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_plane.h:548:5: note: declared here
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/../include/../backport/backport.h:6:0,
                 from <command-line>:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h: In function ‘kcl_drm_calc_vbltimestamp_from_scanoutpos’:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:332:9: error: too many arguments to function ‘drm_calc_vbltimestamp_from_scanoutpos’
  return drm_calc_vbltimestamp_from_scanoutpos(dev, pipe, max_error, vblank_time,
         ^
In file included from ./include/drm/drmP.h:83:0,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/../include/../backport/backport.h:6,
                 from <command-line>:0:
./include/drm/drm_vblank.h:173:6: note: declared here
 bool drm_calc_vbltimestamp_from_scanoutpos(struct drm_device *dev,
      ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.c:1:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h: In function ‘kcl_drm_universal_plane_init’:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:271:29: error: incompatible type for argument 7 of ‘drm_universal_plane_init’
      formats, format_count, type, name);
                             ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.c:1:
./include/drm/drm_plane.h:548:5: note: expected ‘const uint64_t * {aka const long long unsigned int *}’ but argument is of type ‘enum drm_plane_type’
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.c:1:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:271:35: error: incompatible type for argument 8 of ‘drm_universal_plane_init’
      formats, format_count, type, name);
                                   ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.c:1:
./include/drm/drm_plane.h:548:5: note: expected ‘enum drm_plane_type’ but argument is of type ‘const char *’
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.c:1:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:270:10: error: too few arguments to function ‘drm_universal_plane_init’
   return drm_universal_plane_init(dev, plane, possible_crtcs, funcs,
          ^
In file included from ./include/drm/drm_crtc.h:45:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.c:1:
./include/drm/drm_plane.h:548:5: note: declared here
 int drm_universal_plane_init(struct drm_device *dev,
     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.c:1:0:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h: In function ‘kcl_drm_calc_vbltimestamp_from_scanoutpos’:
/var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:332:9: error: too many arguments to function ‘drm_calc_vbltimestamp_from_scanoutpos’
  return drm_calc_vbltimestamp_from_scanoutpos(dev, pipe, max_error, vblank_time,
         ^
In file included from ./include/drm/drmP.h:83:0,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/include/kcl/kcl_drm.h:6,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.c:1:
./include/drm/drm_vblank.h:173:6: note: declared here
 bool drm_calc_vbltimestamp_from_scanoutpos(struct drm_device *dev,
      ^
scripts/Makefile.build:314: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.o' failed
make[2]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl/kcl_drm.o] Error 1
make[2]: *** Waiting for unfinished jobs....
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_doorbell.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_flat_memory.o
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.c: At top level:
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.c:809:2: error: unknown field ‘set_busid’ specified in initializer
  .set_busid = drm_pci_set_busid,
  ^
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.c:809:15: error: ‘drm_pci_set_busid’ undeclared here (not in a function)
  .set_busid = drm_pci_set_busid,
               ^
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.c:814:26: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .get_vblank_timestamp = kcl_amdgpu_get_vblank_timestamp_kms,
                          ^
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.c:814:26: note: (near initialization for ‘kms_driver.get_vblank_timestamp’)
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.c:815:26: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .get_scanout_position = kcl_amdgpu_get_crtc_scanoutpos,
                          ^
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.c:815:26: note: (near initialization for ‘kms_driver.get_scanout_position’)
cc1: some warnings being treated as errors
scripts/Makefile.build:314: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.o' failed
make[2]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu/amdgpu_drv.o] Error 1
scripts/Makefile.build:573: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu' failed
make[1]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdgpu] Error 2
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.o
scripts/Makefile.build:573: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl' failed
make[1]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkcl] Error 2
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_queue.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_mqd_manager.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_mqd_manager_cik.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_mqd_manager_vi.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_mqd_manager_v9.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_kernel_queue.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_kernel_queue_cik.o
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c: In function ‘kfd_process_device_create_obj_handle’:
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c:924:37: error: passing argument 2 of ‘interval_tree_insert’ from incompatible pointer type [-Werror=incompatible-pointer-types]
  interval_tree_insert(&buf_obj->it, &p->bo_interval_tree);
                                     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_priv.h:36:0,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_ipc.h:28,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c:38:
./include/linux/interval_tree.h:15:1: note: expected ‘struct rb_root_cached *’ but argument is of type ‘struct rb_root *’
 interval_tree_insert(struct interval_tree_node *node,
 ^
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c: In function ‘kfd_process_find_bo_from_interval’:
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c:974:37: error: passing argument 1 of ‘interval_tree_iter_first’ from incompatible pointer type [-Werror=incompatible-pointer-types]
  it_node = interval_tree_iter_first(&p->bo_interval_tree,
                                     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_priv.h:36:0,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_ipc.h:28,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c:38:
./include/linux/interval_tree.h:23:1: note: expected ‘struct rb_root_cached *’ but argument is of type ‘struct rb_root *’
 interval_tree_iter_first(struct rb_root_cached *root,
 ^
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c: In function ‘kfd_process_device_remove_obj_handle’:
/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c:1014:37: error: passing argument 2 of ‘interval_tree_remove’ from incompatible pointer type [-Werror=incompatible-pointer-types]
  interval_tree_remove(&buf_obj->it, &p->bo_interval_tree);
                                     ^
In file included from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_priv.h:36:0,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_ipc.h:28,
                 from /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.c:38:
./include/linux/interval_tree.h:19:1: note: expected ‘struct rb_root_cached *’ but argument is of type ‘struct rb_root *’
 interval_tree_remove(struct interval_tree_node *node,
 ^
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_kernel_queue_vi.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_kernel_queue_v9.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_packet_manager.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process_queue_manager.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_device_queue_manager.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_device_queue_manager_cik.o
  CC [M]  /var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_device_queue_manager_vi.o
cc1: some warnings being treated as errors
scripts/Makefile.build:314: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.o' failed
make[2]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd/kfd_process.o] Error 1
make[2]: *** Waiting for unfinished jobs....
scripts/Makefile.build:573: recipe for target '/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd' failed
make[1]: *** [/var/lib/dkms/amdgpu/17.40-492261/build/amd/amdkfd] Error 2
Makefile:1509: recipe for target '_module_/var/lib/dkms/amdgpu/17.40-492261/build' failed
make: *** [_module_/var/lib/dkms/amdgpu/17.40-492261/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.14.0-041400-generic'

```

If i reboot without un-installing the driver, I get the ubuntu login page, but every time I try it just kicks me out. 

Any ideas?

---

### Post by scarfguy on 2018-02-18
Yes, I just had the same problem. To get back into your system you will have to press ctrl + alt + F1 - F6 at the login screen. This should bring you to a Terminal. If all you get is a black screen, you can either fix it blind or edit the grub file in /etc/default/grub (or boot with a temporary file) with some sort of rescue cd. There will be a line beginning with "linux". Change the words "quiet splash" to "text". Now you should get the Terminal.

There is a new vesion of the driver: 17.50. This did work for me.

---

### Post by Linux_cat on 2018-02-18
Thanks, I did uninstall the driver so I am using the standard Radeon driver for now..

I cant seem to find the 17.50 driver the link on the site points to: [https://www2.ati.com/drivers/linux/ubuntu/amdgpu-pro-17.50-511655.tar.xz](https://www2.ati.com/drivers/linux/ubuntu/amdgpu-pro-17.50-511655.tar.xz) which is dead. Do you have a link for the latest driver?

---

### Post by scarfguy on 2018-02-18
Using this one [https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx](https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx) and it works. (but I can't figure out how to turn off vsync)

---

