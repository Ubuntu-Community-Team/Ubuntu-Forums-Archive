---
title: "USB Pen Drive Issues"
date: 2008-06-27
forum: Hardware
---

### Post by BenAshton24 on 2008-06-27
Right, so a while back i attempted to install Ubuntu 7.10 on my USB pen drive using instructions from pendrivelinux.com. it didn't work for whatever reason and now i cannot format my pen drive :S in gparted it says that there is 1.36gb of space when it is an 8 gb drive and when i try to create a partition on the free space, gparted crashes. i launched gparted from terminal and this is the output before it crashed:
========================================================================
Unable to open /dev/sdi - unrecognised disk label.
Device /dev/sdi has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Unable to open /dev/sdi - unrecognised disk label.
*** stack smashing detected ***: gparted terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb730c138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb730c0f0]
/lib/libparted-1.7.so.1[0xb7f335b4]
/lib/libparted-1.7.so.1[0xb7f22c18]
[0xb1d789c0]
========================================================================
I also tried it from command line with fdisk but that to failed with the following output:
========================================================================
fdisk /dev/sdi
Warning: Device /dev/sdi has a logical sector size of 2048.  Not all parts of
GNU Parted support this at the moment, and the working code is HIGHLY
EXPERIMENTAL.

Error: Unable to open /dev/sdi - unrecognised disk label.                 
========================================================================

I'm not sure what else to try, please help :D thanx.

---

### Post by matthewpetty on 2009-10-25
> **BenAshton24 said:**
> Right, so a while back i attempted to install Ubuntu 7.10 on my USB pen drive using instructions from pendrivelinux.com. it didn't work for whatever reason and now i cannot format my pen drive :S in gparted it says that there is 1.36gb of space when it is an 8 gb drive and when i try to create a partition on the free space, gparted crashes. i launched gparted from terminal and this is the output before it crashed:
========================================================================
Unable to open /dev/sdi - unrecognised disk label.
Device /dev/sdi has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Unable to open /dev/sdi - unrecognised disk label.
*** stack smashing detected ***: gparted terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb730c138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb730c0f0]
/lib/libparted-1.7.so.1[0xb7f335b4]
/lib/libparted-1.7.so.1[0xb7f22c18]
[0xb1d789c0]
========================================================================
I also tried it from command line with fdisk but that to failed with the following output:
========================================================================
fdisk /dev/sdi
Warning: Device /dev/sdi has a logical sector size of 2048.  Not all parts of
GNU Parted support this at the moment, and the working code is HIGHLY
EXPERIMENTAL.

Error: Unable to open /dev/sdi - unrecognised disk label.                 
========================================================================

I'm not sure what else to try, please help :D thanx.

I'm having the same problem with an iPod I'm trying to format. Anyone have an answer?

---

