---
title: "Lubuntu 12.04 ATI FGLRX graphics driver AWOL, Acer Aspire 725"
date: 2012-07-25
forum: Hardware
---

### Post by casbahdk on 2012-07-25
I am having problems with installing the ATI/AMD proprietary FGLRX graphics driver (post-release updates). I can succesfully install the ATI/AMD proprietary FGLRX graphics driver, but when I try to install the post-release updates, the driver seems to uninstall. I am not sure how much of the following is necessary, but here is what appears to be relevant from /var/log/jockey.log:```
2012-07-25 11:49:23,395 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:49:23,396 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-25 11:49:23,808 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:49:23,809 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:49:23,938 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:49:23,939 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:49:24,150 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-07-25 11:49:24,470 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-07-25 11:49:31,070 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:49:31,071 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:49:37,516 DEBUG: Installing package: fglrx-updates
2012-07-25 11:49:41,228 DEBUG: install progress dpkg-exec 0.000000
2012-07-25 11:49:43,389 DEBUG: install progress fglrx-amdcccle 0.000000
2012-07-25 11:49:43,445 DEBUG: install progress fglrx-amdcccle 6.250000
2012-07-25 11:49:43,447 DEBUG: install progress fglrx-amdcccle 12.500000
2012-07-25 11:49:43,678 DEBUG: install progress fglrx-amdcccle 18.750000
2012-07-25 11:49:44,046 DEBUG: install progress fglrx 18.750000
2012-07-25 11:49:44,148 DEBUG: install progress fglrx 25.000000
2012-07-25 11:50:04,056 DEBUG: install progress fglrx 31.250000
2012-07-25 11:50:04,815 DEBUG: install progress fglrx 37.500000
2012-07-25 11:50:04,950 DEBUG: install progress ureadahead 37.500000
2012-07-25 11:50:05,095 DEBUG: install progress initramfs-tools 37.500000
2012-07-25 11:50:34,569 DEBUG: install progress libc-bin 37.500000
2012-07-25 11:50:34,938 DEBUG: install progress dpkg-exec 37.500000
2012-07-25 11:50:36,067 DEBUG: install progress fglrx-updates 37.500000
2012-07-25 11:50:36,068 DEBUG: install progress fglrx-updates 43.750000
2012-07-25 11:50:45,810 DEBUG: install progress fglrx-updates 50.000000
2012-07-25 11:50:45,879 DEBUG: install progress fglrx-updates 56.250000
2012-07-25 11:50:46,116 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2012-07-25 11:50:46,218 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2012-07-25 11:50:46,856 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2012-07-25 11:50:46,919 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2012-07-25 11:50:46,995 DEBUG: install progress ureadahead 75.000000
2012-07-25 11:50:47,302 DEBUG: install progress dpkg-exec 75.000000
2012-07-25 11:50:47,385 DEBUG: install progress fglrx-updates 75.000000
2012-07-25 11:50:47,708 DEBUG: install progress fglrx-updates 81.250000
2012-07-25 11:51:21,577 DEBUG: install progress fglrx-updates 87.500000
2012-07-25 11:51:21,821 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2012-07-25 11:51:21,899 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2012-07-25 11:51:21,977 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-07-25 11:51:22,056 DEBUG: install progress initramfs-tools 100.000000
2012-07-25 11:51:48,840 DEBUG: install progress libc-bin 100.000000
2012-07-25 11:51:50,652 DEBUG: (Reading database ... 140308 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-updates.
(Reading database ... 140037 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
Building only for 3.2.0-27-generic
Building for architecture x86_64
Building initial module for 3.2.0-27-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-27-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-07-25 11:51:51,172 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-07-25 11:52:44,979 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:44,980 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:52:45,035 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:45,035 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:52:55,026 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:55,026 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:52:55,081 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:55,082 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:52:55,304 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-07-25 11:52:55,627 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-07-25 11:52:55,731 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:55,731 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-25 11:52:56,180 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:56,181 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:52:56,235 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:56,236 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:52:56,382 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:56,382 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:52:56,437 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:52:56,438 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:52:56,656 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-07-25 11:52:56,988 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-07-25 11:53:03,590 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-25 11:53:03,591 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-25 12:02:27,953 DEBUG: Shutting down
```

---

