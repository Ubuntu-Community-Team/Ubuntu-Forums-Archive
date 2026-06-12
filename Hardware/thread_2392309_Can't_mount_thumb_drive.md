---
title: "Can't mount thumb drive"
date: 2018-05-19
forum: Hardware
---

### Post by rtroxel2 on 2018-05-19
I'm trying to mount a thumb drive on my Ubuntu 16.04 LTS machine, but keep receiving the following message:

Error mounting /dev/sdc1 at /media/roy/USB30FD: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdc1" "/media/roy/USB30FD"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

Does this mean I have to change the file system on the thumbdrive? The current system is compatible with Windows 10.

My other machine specs are:


7.8 GiB memory
Pentium(R) Dual-Core CPU E6500 @ 2.93GHz × 2 processor
AMD RV730 (DRM 2.43.0 / 4.4.0-124-generic, LLVM 5.0.0) graphics card
64-bit Ubuntu 16.04 
306.5 GB Hrd drive

Thanks,
Roy

---

### Post by TheFu on 2018-05-19
exfat is a patent encumbered file system from microsoft.  Whether you should or shouldn't use it is completely up to you.  I won't, but that's me.  Win10 is compatible with lots of other file systems, though not natively with any Linux file systems.

I think there is an exfat driver available for Linux, you might just need to install that.
If you run **mount.exfat** in a terminal, it should say which package needs to be installed. In theory.

BTW, if you want the best performance, don't use a GUI to mount storage. For quick things, it isn't an issue, but if you have multi-GB of data to be transferred or want to run programs off the device, the difference is noticeable.

---

### Post by yancek on 2018-05-19
exfat is not a very common filesystem and I am not aware of any Linux system which has drivers for it in a default install primarily because it is not used much.  You should be able to install with this command what you need.

> sudo apt-get install exfat-fuse exfat-utils

---

