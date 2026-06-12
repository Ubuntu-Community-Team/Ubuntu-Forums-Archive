---
title: "Since 14.04 upgrade Nvidia ION drivers fail to work"
date: 2015-01-04
forum: Hardware
---

### Post by mc@2 on 2015-01-04
I just upgraded my Nvidia ion based XMBC-box from 13.04 to 14.04 (stupid, never fix something that aint broken) and after the reboot i got "XBMC needs hardware accelerated opengl rendering".

Digging i little deeper i found "(EE) Failed to load module "nvidia" (module-specific error, 0)" in my Xorg.0.log.

I used the instructions here: [http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/) and learned i needed nvidia-340 drivers. Using the org-edgers ppa in installed them (and thus removing nvidia-current), but still had the same errors. I tried loading the module myself but got:
```
root@htpc:/# modprobe nvidia
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_340'
modprobe: ERROR: could not insert 'nvidia_340': Function not implemented
```

I looked back at the out-put of apt-gt install and saw
```
First Installation: checking all kernels...
Building for 3.2.0-63-generic-pae and 3.13.0-43-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.13.0-43-generic
Done.
```
I tried installing the headers:
```
root@htpc:/# apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.2.0-63-generic-pae
E: Couldn't find any package by regex 'linux-headers-3.2.0-63-generic-pae'
root@htpc:/# apt-get install linux-headers-3.2.0-63
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.2.0-63
E: Couldn't find any package by regex 'linux-headers-3.2.0-63'

```
Any suggestions how to go from here? 

Some data:
```
root@htpc:/# uname -a
Linux htpc 3.2.0-63-generic-pae #95-Ubuntu SMP Thu May 15 23:26:11 UTC 2014 i686 i686 i686 GNU/Linux

root@htpc:/# lspci -vnn | grep -i VGA -A 12
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation ION VGA [10de:087d] (rev b1) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device [1043:83e2]
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f6000000 (64-bit, prefetchable) [size=32M]
        I/O ports at dc00 [size=128]
        Expansion ROM at fbee0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Kernel modules: nouveau, nvidiafb

```

---

### Post by Yellow Pasque on 2015-01-05
You're still booting into an old kernel (llooks like it was from precise/12.04). Boot into the 3.13.0-43-generic kernel and get rid of the old 3.2.x one. Hopefully, that will fix your issue.

---

### Post by mc@2 on 2015-01-05
Thanks for your reply. Right after posting this I noticed it too and tried updating grub, but that was not a big success: [http://ubuntuforums.org/showthread.php?t=2259462](http://ubuntuforums.org/showthread.php?t=2259462)

---

### Post by A_good_user on 2015-01-05
Is it possible to downgrade ubuntu-drivers-common to 0.2.91.5?

---

### Post by mc@2 on 2015-01-05
[Temüjin]("http://ubuntuforums.org/member.php?u=327594") was right, after quite some struggle (again see [http://ubuntuforums.org/showthread.php?t=2259462](http://ubuntuforums.org/showthread.php?t=2259462)) i managed to boot into 3.13.0-43 and everything works fine again! BTW, i'm using nvidia-340, not nvidia-current.

---

### Post by spyderdyne on 2015-09-28
I have the same issue after forcing a kernel upgrade to support a TV Tuner card driver for MythTV:

```

root@Ayana-Angel:~# uname -a
Linux Ayana-Angel 4.2.0-040200-generic #201508301530 SMP Sun Aug 30 19:31:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

oot@Ayana-Angel:~# cat /etc/issue
Ubuntu 15.04 \n \l

```

Will try to unload the proprietary tested driver and load the generic supported driver.  Here is the output/error:

```

root@Ayana-Angel:~# sudo startx
xauth:  file /root/.Xauthority does not exist


X.Org X Server 1.17.1
Release Date: 2015-02-10
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
Current Operating System: Linux Ayana-Angel 4.2.0-040200-generic #201508301530 SMP Sun Aug 30 19:31:40 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-040200-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash
Build Date: 11 September 2015  10:30:58AM
xorg-server 2:1.17.1-0ubuntu3.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.32.6
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Sep 28 09:59:03 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
modprobe: ERROR: ../libkmod/libkmod-module.c:816 kmod_module_insert_module() could not find module by name='nvidia_340'
modprobe: ERROR: could not insert 'nvidia_340': Function not implemented
xinit: connection to X server lost

waiting for X server to shut down error setting MTRR (base = 0xf1000000, size = 0x00e00000, type = 1) Invalid argument (22)
(II) Server terminated successfully (0). Closing log file.

```

This is probably to be expected since I am running a bleeding edge kernel, but I thought I would mention it here anyway since it seems to apply to these drivers and will probably require NVidia to provide a different one soon to address the issue.  I have to use the vendor driver for my HTPC video card's HDMI audio to work correctly.

After searching apt for a more recent driver I found the latest one:

```

root@Ayana-Angel:~# apt-cache search nvidia

nvidia-340 - NVIDIA binary driver - version 340.76
nvidia-340-dev - NVIDIA binary Xorg driver development files
nvidia-340-updates - NVIDIA binary driver - version 340.76
nvidia-340-updates-dev - NVIDIA binary Xorg driver development files
nvidia-340-updates-uvm - Transitional package for nvidia-340-updates
nvidia-340-uvm - Transitional package for nvidia-340
nvidia-346 - NVIDIA binary driver - version 346.59
nvidia-346-dev - NVIDIA binary Xorg driver development files
nvidia-346-updates - NVIDIA binary driver - version 346.59
nvidia-346-updates-dev - NVIDIA binary Xorg driver development files
nvidia-346-updates-uvm - Transitional package for nvidia-346-updates
nvidia-346-uvm - Transitional package for nvidia-346

```

Installed the latest:

```

root@Ayana-Angel:~# apt-get install nvidia-346
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-28-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcuda1-346 nvidia-opencl-icd-346
The following packages will be REMOVED:
  libcuda1-340 nvidia-340 nvidia-opencl-icd-340
The following NEW packages will be installed:
  libcuda1-346 nvidia-346 nvidia-opencl-icd-346
0 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.
Need to get 72.5 MB of archives.
After this operation, 9,661 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/restricted libcuda1-346 amd64 346.59-0ubuntu1 [7,742 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid/restricted nvidia-346 amd64 346.59-0ubuntu1 [56.9 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ vivid/restricted nvidia-opencl-icd-346 amd64 346.59-0ubuntu1 [7,827 kB]
Fetched 72.5 MB in 7s (9,726 kB/s)                                             
(Reading database ... 247106 files and directories currently installed.)
Removing libcuda1-340 (340.76-0ubuntu2) ...
Removing nvidia-340 (340.76-0ubuntu2) ...
Stopping nvidia-persistenced
nvidia-persistenced: no process found
Done.
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-340-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-340-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Removing nvidia-opencl-icd-340 (340.76-0ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-040200-generic
Selecting previously unselected package libcuda1-346.
(Reading database ... 246815 files and directories currently installed.)
Preparing to unpack .../libcuda1-346_346.59-0ubuntu1_amd64.deb ...
Unpacking libcuda1-346 (346.59-0ubuntu1) ...
Selecting previously unselected package nvidia-346.
Preparing to unpack .../nvidia-346_346.59-0ubuntu1_amd64.deb ...
Unpacking nvidia-346 (346.59-0ubuntu1) ...
Selecting previously unselected package nvidia-opencl-icd-346.
Preparing to unpack .../nvidia-opencl-icd-346_346.59-0ubuntu1_amd64.deb ...
Unpacking nvidia-opencl-icd-346 (346.59-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.0.2-5) ...
Setting up libcuda1-346 (346.59-0ubuntu1) ...
Setting up nvidia-346 (346.59-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-346/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-346/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-346/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-346
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 135) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-346-346.59 DKMS files...
First Installation: checking all kernels...
Building only for 4.2.0-040200-generic
Building for architecture x86_64
Building initial module for 4.2.0-040200-generic
ERROR (dkms apport): kernel package linux-headers-4.2.0-040200-generic is not supported
Error! Bad return status for module build on kernel: 4.2.0-040200-generic (x86_64)
Consult /var/lib/dkms/nvidia-346/346.59/build/make.log for more information.
Setting up nvidia-opencl-icd-346 (346.59-0ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-040200-generic

```

After reboot I have the same issue.  Unable to log in to the GUI.  It accepts my password, the drops to a black error screen and takes me back to the login.  Removed the proprietary driver completely to attempt to get Ubuntu to pick the Nouveau driver.

```

root@Ayana-Angel:~# apt-get remove nvidia-346
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-28-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-346
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 283 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 247132 files and directories currently installed.)
Removing nvidia-346 (346.59-0ubuntu1) ...
Stopping nvidia-persistenced
nvidia-persistenced: no process found
Done.
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-346-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-346-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-346
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-040200-generic

```

It works!  Yay!  In fact, the Ubuntu default drivers actually work with the new kernel!

Winning!!!

---

