---
title: "Fingerprint Scanner FCP 1020"
date: 2018-08-26
forum: Hardware
---

### Post by psctec on 2018-08-26
Hi,

My fingerprint scanner isn't reconized.
lsub not show vendor name

10a5:0007

Is an FPC Controller AB ou FPC 1020

I tried compile the driver found in [https://github.com/SanniZ/fpc1020-driver](https://github.com/SanniZ/fpc1020-driver) and i get the following errors:

```


make -C /lib/modules/4.15.0-32-generic/build M=/fpc1020-driver-master modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-32-generic'
CC [M] /fpc1020-driver-master/fpc1020_main.o
In file included from ./include/linux/kernel.h:15:0,
from ./include/linux/list.h:9,
from ./include/linux/module.h:9,
from /fpc1020-driver-master/fpc1020_main.c:13:
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:238:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, adc_gain, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:239:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, adc_shift, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:240:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, capture_mode, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:241:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, capture_count, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:242:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, capture_settings_mux, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:243:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, pxl_ctrl, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:244:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, capture_row_start, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:245:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, capture_row_count, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:246:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, capture_col_start, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:247:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(setup, capture_col_groups, DEVFS_SETUP_MODE);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:273:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(diag, spi_register, DEVFS_DIAG_MODE_RW);
^~~~~~~~~~~~~~~~
./include/linux/build_bug.h:30:45: error: negative width in bit-field ‘’
#define BUILD_BUG_ON_ZERO(e) (sizeof(struct { int:(-!!(e)); }))
^
./include/linux/kernel.h:967:3: note: in expansion of macro ‘BUILD_BUG_ON_ZERO’
BUILD_BUG_ON_ZERO((perms) & 2) + 
^~~~~~~~~~~~~~~~~
./include/linux/sysfs.h:103:12: note: in expansion of macro ‘VERIFY_OCTAL_PERMISSIONS’
.mode = VERIFY_OCTAL_PERMISSIONS(_mode) }, 
^~~~~~~~~~~~~~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:226:10: note: in expansion of macro ‘__ATTR’
.attr = __ATTR(__field, (__mode), 
^~~~~~
/fpc1020-driver-master/fpc1020_main.c:234:6: note: in expansion of macro ‘FPC1020_ATTR’
FPC1020_ATTR(_grp, _field, (_mode))
^~~~~~~~~~~~
/fpc1020-driver-master/fpc1020_main.c:275:8: note: in expansion of macro ‘FPC1020_DEV_ATTR’
static FPC1020_DEV_ATTR(diag, spi_data , DEVFS_DIAG_MODE_RW);
^~~~~~~~~~~~~~~~
scripts/Makefile.build:332: recipe for target '/fpc1020-driver-master/fpc1020_main.o' failed
make[2]: *** [/fpc1020-driver-master/fpc1020_main.o] Error 1
Makefile:1552: recipe for target 'module/fpc1020-driver-master' failed
make[1]: *** [module/fpc1020-driver-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-32-generic'
Makefile:27: recipe for target 'modules' failed
make: *** [modules] Error 2

```

Fingerprint-gui doesn't reconize too

Any Help?

Thanks,

Paulo

---

### Post by foro.carlos on 2018-12-13
I'm in the same boat.
I'll try myself to compile and i'll come back with the results.

---

### Post by KhaimovMR on 2019-08-13
Same thing. Have no luck compiling.

---

