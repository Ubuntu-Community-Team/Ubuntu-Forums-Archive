---
title: "ATI ES1000 driver in 12.04 LTS x64"
date: 2012-12-18
forum: Hardware
---

### Post by zigwaldo on 2012-12-18
Posted this over a week ago, didn't get a single reply, so figured I might try again before moving on.

I have a sc1430 dell server with  an integrated ATI ES10000 

> lspci | grep VGA 09:09.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI ES1000 (rev 02)
I have configured the server as a home media server and need the  desktop display because some of the applications I use are not  manageable from CLI. Currently using GDM with cinnamon desktop. I've  tried lightdm with both unity *gags* and gnome. The issue I'm having is  the contrast is extremely high (yes I've tried adjusting my monitor)  making it hard to read a lot of content (attached screen shot). Below is  the output of attempting to install the fglrx driver which through what  I've read is supposed to work but I've had no success.

> root@**:~# sudo apt-get install fglrx fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  usb-modeswitch dnsmasq-base usb-modeswitch-data libnetfilter-conntrack3 iputils-arping libnl-route-3-200
  modemmanager python-wicd libsysfs2 wicd-daemon wicd-gtk
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.5 MB of archives.
After this operation, 220 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted fglrx amd64 2:8.960-0ubuntu1.1 [66.6 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted fglrx-amdcccle amd64 2:8.960-0ubuntu1.1 [5,924 kB]
Fetched 72.5 MB in 58s (1,250 kB/s)                                                                               
Selecting previously unselected package fglrx.
(Reading database ... 175964 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1.1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.960-0ubuntu1.1_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up fglrx (2:8.960-0ubuntu1.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide  /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in  auto mode.
update-alternatives: warning: skip creation of  /etc/OpenCL/vendors/amdocl32.icd because associated file  /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group  x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide  /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in  auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-34-generic
Building for architecture x86_64
Building initial module for 3.2.0-34-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-34-generic/updates/dkms/

depmod...................................

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.960-0ubuntu1.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@**:~# sudo aticonfig --initial
aticonfig: No supported adapters detected
root@**:~# sudo amdconfig --initial
amdconfig: No supported adapters detected 			 		

Any help would be greatly appreciated!

---

### Post by QIII on 2012-12-18
Unfortunately, that is no longer supported by the fglrx driver in Linux and hasn't been since about the 8.xx driver series (2008).

That's why you are seeing the message about it being unsupported.

You'll need to use the open source Radeon driver.

Uninstall fglrx.

If the Radeon driver is not working (which the developers say it should) you may have a hardware issue besides.

---

