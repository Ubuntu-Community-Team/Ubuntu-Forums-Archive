---
title: "Dell XPS15 9550 With Kernel 4.6"
date: 2016-05-09
forum: Hardware
---

### Post by wundbread on 2016-05-09
I just wanted to share that nearly every issue I had with Ubuntu 16.04 on my Dell XPS15 is solved by using a vanilla 4.6 kernel.

The issue with freezes when plugging in a HDMI monitor are completely gone, and with rc7 I no longer need to remove and re-insert the brcmfmac module.

Just go to:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc7-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc7-wily/)

Download the amd64 debs and install with dpkg -i *.deb.

The only issue left is the "no sound with headphones" issue, which I found and easy workaround.   

[LIST=1]
[*]Plug in the headphones
[*]Suspend
[*]Wake Up the computer
[/LIST]

And then it should just work.

Only potential downside is that the proprietary nvidia drivers are not yet compatible with 4.6.

---

### Post by jeremy31 on 2016-05-09
You could help others by booting into a supported 4.4 kernel and filing a bug report, see [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

In the bug report you can say using the 4.6 kernel fixes your issues with HDMI, and create a second bug report about the wireless issue with brcmfmac

You will likely need to file the bug reports against package linux

RE: potential downside is why Ubuntu has it's own kernels in order to have some stability

---

### Post by stefanmaric on 2016-05-16
I have a XPS 15 9550 and tried to install the final version of kernel 4.6 but got this error:

```

$ cat /var/lib/dkms/tp-smapi/0.41/build/make.log
DKMS make.log for tp-smapi-0.41 for kernel 4.6.0-040600-generic (x86_64)
lun may 16 03:50:23 VET 2016
make: Entering directory '/usr/src/linux-headers-4.6.0-040600-generic'
  LD      /var/lib/dkms/tp-smapi/0.41/build/built-in.o
  CC [M]  /var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.o
In file included from include/linux/module.h:18:0,
                 from /var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c:33:
/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c: In function ‘__check_force_io’:
include/linux/moduleparam.h:344:67: error: return from incompatible pointer type [-Werror=incompatible-pointer-types]
  static inline type __always_unused *__check_##name(void) { return(p); }
                                                                   ^
include/linux/moduleparam.h:396:35: note: in expansion of macro ‘__param_check’
 #define param_check_bool(name, p) __param_check(name, p, bool)
                                   ^
include/linux/moduleparam.h:146:2: note: in expansion of macro ‘param_check_bool’
  param_check_##type(name, &(value));       \
  ^
/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c:100:1: note: in expansion of macro ‘module_param_named’
 module_param_named(force_io, force_io, bool, 0600);
 ^
/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c: In function ‘check_dmi_for_ec’:
/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c:469:1: warning: the frame size of 1728 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
cc1: some warnings being treated as errors
scripts/Makefile.build:297: recipe for target '/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.o' failed
make[1]: *** [/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.o] Error 1
Makefile:1433: recipe for target '_module_/var/lib/dkms/tp-smapi/0.41/build' failed
make: *** [_module_/var/lib/dkms/tp-smapi/0.41/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.6.0-040600-generic'

```

---

