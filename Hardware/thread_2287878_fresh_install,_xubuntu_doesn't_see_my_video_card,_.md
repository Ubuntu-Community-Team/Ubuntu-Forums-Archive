---
title: "fresh install, xubuntu doesn't see my video card, no additional drivers available"
date: 2015-07-22
forum: Hardware
---

### Post by finny388 on 2015-07-22
Just did a fresh install of xubuntu 14.04.2
enabled proprietary ppas during install
did updates until there were no more (took 2 rounds)
only 1280 by 768 available in display settings (i think that was it. but only one res available)

go to system/additional drivers and it checks briefly then reports "no additional drivers available"
in repositories Partner ppa's weren't enabled. I enabled them. update/upgraded. no change.

on another partition I have my main os running, Kubuntu 14.10, and it has no problems.

Here is the output of lspci on both systems:

```

[COLOR="#0000FF"]Xubuntu 14.04.2
[/COLOR]$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation [COLOR="#FF0000"]Device 13c2[/COLOR] (rev a1)

[COLOR="#0000FF"]Kubuntu 14.10[/COLOR]
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation [COLOR="#FF0000"]GM204 [GeForce GTX 970][/COLOR] (rev a1)

```

not sure what to do now. could this have to do with the startup scripts? my display is a TV and I have to change any new boot scripts (when in grub) from 'quiet splash' to 'nomodeset' or they won't boot. also in some new installs I have to manually set DPI in xorg.conf to prevent miniscule text. only had to edit grub in this case.

---

### Post by kerry_s on 2015-07-22
basically it's a newer vid card, so the newer the *ubuntu/kernel the better supported.

xubuntu 14.04 is older than your kubuntu 14.10.

i'd recommend you try xubuntu 15.04, it's the newest release with a more updated kernel for better support of new hardware & has all the new xfce4 features.

nomodeset is it uses the vesa driver to hopefully get a working display. you may not need that in more updated kernels with better drivers.

---

### Post by finny388 on 2015-07-22
thanks kerry

re: nomodeset, I'm using 3.16.0-43-generic on kubuntu, guess I've got to go newer than that

regarding xubuntu 14.04.2
I installed this to get familiar again (used to use xubuntu until I got my new rig) because I'm about to update a friend who I've got running 12.04 which is way past due upgrading
and my brother wants to resurrect his 2009 iMac so I had this LTS version in mind for both.

geez, I don't need 3d or anything, I just want 1080.

you'd think the integrated intel or whatever it thinks my nvidia card is could handle that.

:(

---

### Post by kerry_s on 2015-07-22
well the last time i was using xubuntu, you could install kernels from other versions. look in synaptic, you might be able to do the 14.04 with a 15.04 kernel which should give you the updated drivers you need.

i to was doing something for a friend, i made a 64bit debian testing net installer with firmware, the only way to test it was to install, so i'm on debian testing xfce currently, till i get my usb back, then i may or may not go back to xubuntu 15.04.

i'm kinda liking the debian version, its not as easy as xubuntu, but i have enough experience it's not really a issue for me.
it seems because debian is done so basic, things are just so much faster. i'm on a old hp-mini 210-1010nr netbook, 2x atom 1.6ghz & 2gb ram(maxed), i may just choose speed over convenience. lol

---

### Post by finny388 on 2015-07-25
The xubuntu 14.04.2 install uses 3.16.00-44
The kubuntu 14.20 uses 3.16.00-43

14.04.2 just came out this year and my hardware is all 2014 (GTX 970)

So still don't understand what is going on

---

### Post by Yellow Pasque on 2015-07-25
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1351699](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1351699)

So, for Xubuntu 14.04.2, you probably want to use a PPA, because Ubuntu tends to lag behind in supporting really recent Nvidia cards. [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

Also, this won't fix anything, but it should give you updated human-readable names for lspci to use:
```
sudo update-pciids
```

---

### Post by finny388 on 2015-07-25
I feel like this a great learning opportunity

this must go beyond the kernel if my older kernel, newer distro release (14.10, 3.16.00-43) found nvidia drivers, installed, I didn't even give it much thought
while 14.04.2 xubuntu 3.16.00-44 fails.

thanks for the reply and links
i will try the marley ppa
what happened to x-swat?

---

### Post by finny388 on 2015-07-25
after update pciid the lspci are equal now. both say GM204 [GeForce GTX 970]

added the marley ppa
update
then
```
$ sudo apt-get install nvidia-current nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot lib32gcc1 libc6-i386 libcuda1-304 libfakeroot libvdpau1
  nvidia-304 nvidia-libopencl1-304 nvidia-opencl-icd-304
  screen-resolution-extra
Suggested packages:
  dpkg-dev debhelper nvidia-vdpau-driver vdpau-driver
The following NEW packages will be installed:
  dkms fakeroot lib32gcc1 libc6-i386 libcuda1-304 libfakeroot libvdpau1
  nvidia-304 nvidia-current nvidia-libopencl1-304 nvidia-opencl-icd-304
  nvidia-settings screen-resolution-extra
0 upgraded, 13 newly installed, 0 to remove and 1 not upgraded.
Need to get 51.2 MB of archives.
After this operation, 225 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main dkms all 2.2.0.3-1.1ubuntu5.14.04.1 [64.6 kB]
Get:2 http://ppa.launchpad.net/mamarley/nvidia/ubuntu/ trusty/main libvdpau1 amd64 1.1-0ubuntu0~ppa0~trusty0 [25.5 kB]
Get:3 http://ppa.launchpad.net/mamarley/nvidia/ubuntu/ trusty/main nvidia-settings amd64 352.21-100ubuntu100~ppa1~trusty0 [946 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ trusty/main libfakeroot amd64 1.20-3ubuntu2 [25.4 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ trusty/main fakeroot amd64 1.20-3ubuntu2 [55.0 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libc6-i386 amd64 2.19-0ubuntu6.6 [2,206 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/restricted libcuda1-304 amd64 304.125-0ubuntu0.0.1 [6,416 kB]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main lib32gcc1 amd64 1:4.9.1-0ubuntu1 [47.6 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-304 amd64 304.125-0ubuntu0.0.1 [35.5 MB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-current amd64 304.125-0ubuntu0.0.1 [4,414 B]
Get:11 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-libopencl1-304 amd64 304.125-0ubuntu0.0.1 [16.1 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-opencl-icd-304 amd64 304.125-0ubuntu0.0.1 [5,809 kB]
Get:13 http://ca.archive.ubuntu.com/ubuntu/ trusty/main screen-resolution-extra all 0.17.1 [11.4 kB]
Fetched 51.2 MB in 22s (2,281 kB/s)                                            
Selecting previously unselected package libvdpau1:amd64.
(Reading database ... 173415 files and directories currently installed.)
Preparing to unpack .../libvdpau1_1.1-0ubuntu0~ppa0~trusty0_amd64.deb ...
Unpacking libvdpau1:amd64 (1.1-0ubuntu0~ppa0~trusty0) ...
Selecting previously unselected package dkms.
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.1_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.1) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20-3ubuntu2) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking fakeroot (1.20-3ubuntu2) ...
Selecting previously unselected package libc6-i386.
Preparing to unpack .../libc6-i386_2.19-0ubuntu6.6_amd64.deb ...
Unpacking libc6-i386 (2.19-0ubuntu6.6) ...
Selecting previously unselected package libcuda1-304.
Preparing to unpack .../libcuda1-304_304.125-0ubuntu0.0.1_amd64.deb ...
Unpacking libcuda1-304 (304.125-0ubuntu0.0.1) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a4.9.1-0ubuntu1_amd64.deb ...
Unpacking lib32gcc1 (1:4.9.1-0ubuntu1) ...
Selecting previously unselected package nvidia-304.
Preparing to unpack .../nvidia-304_304.125-0ubuntu0.0.1_amd64.deb ...
Unpacking nvidia-304 (304.125-0ubuntu0.0.1) ...
Selecting previously unselected package nvidia-current.
Preparing to unpack .../nvidia-current_304.125-0ubuntu0.0.1_amd64.deb ...
Unpacking nvidia-current (304.125-0ubuntu0.0.1) ...
Selecting previously unselected package nvidia-libopencl1-304.
Preparing to unpack .../nvidia-libopencl1-304_304.125-0ubuntu0.0.1_amd64.deb ...
Unpacking nvidia-libopencl1-304 (304.125-0ubuntu0.0.1) ...
Selecting previously unselected package nvidia-opencl-icd-304.
Preparing to unpack .../nvidia-opencl-icd-304_304.125-0ubuntu0.0.1_amd64.deb ...
Unpacking nvidia-opencl-icd-304 (304.125-0ubuntu0.0.1) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_352.21-100ubuntu100~ppa1~trusty0_amd64.deb ...
Unpacking nvidia-settings (352.21-100ubuntu100~ppa1~trusty0) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Setting up libvdpau1:amd64 (1.1-0ubuntu0~ppa0~trusty0) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.1) ...
Setting up libfakeroot:amd64 (1.20-3ubuntu2) ...
Setting up fakeroot (1.20-3ubuntu2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libc6-i386 (2.19-0ubuntu6.6) ...
Setting up libcuda1-304 (304.125-0ubuntu0.0.1) ...
Setting up lib32gcc1 (1:4.9.1-0ubuntu1) ...
Setting up nvidia-304 (304.125-0ubuntu0.0.1) ...
update-alternatives: using /usr/lib/nvidia-304/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-304/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-304/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-304
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Loading new nvidia-304-304.125 DKMS files...
First Installation: checking all kernels...
Building only for 3.16.0-44-generic
Building for architecture x86_64
Building initial module for 3.16.0-44-generic
Done.

nvidia_304:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-44-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-current (304.125-0ubuntu0.0.1) ...
Setting up nvidia-libopencl1-304 (304.125-0ubuntu0.0.1) ...
Setting up nvidia-opencl-icd-304 (304.125-0ubuntu0.0.1) ...
Setting up screen-resolution-extra (0.17.1) ...
Setting up nvidia-settings (352.21-100ubuntu100~ppa1~trusty0) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-44-generic
```

rebooted
no change in Dispay settings
no change in nVidia settings

:sad:

---

### Post by oldfred on 2015-07-25
If it installed -304 that is now a legacy driver for old nVidia cards.
And when ever you install a new nVidia driver from another source you must totally purge all old nvidia drivers & settings. They seem to conflict.
 #Remove nvidia
sudo apt-get purge nvidia-*

       The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[URL="http://ubuntuforums.org/showthread.php?t=2259210"]http://ubuntuforums.org/showthread.php?t=2259210
[/URL]
 Asus z97-A with nVidia GTX 970 Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896)

No idea which ppa may be better, or even if any real difference.
      Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)

    PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)

    [URL="http://ubuntuforums.org/showthread.php?t=2259210"]
[/URL]

---

### Post by Yellow Pasque on 2015-07-25
You can remove the old 304 driver, as oldfred pointed out:
```
sudo apt-get purge libcuda1-304 nvidia-304 nvidia-current nvidia-libopencl1-304 nvidia-opencl-icd-304 nvidia-settings screen-resolution-extra libvdpau1
```

Instead of nvidia-current, you want nvidia-352:
```
sudo apt-get install nvidia-352
```

> after update pciid the lspci are equal now. both say GM204 [GeForce GTX 970]
Like I said, that's just an aesthetic thing for humans. I'm not aware of any programs that actually use the PCI text name instead of the hex ID (e.g. 1234:abcd) for anything.

---

### Post by finny388 on 2015-07-25
Did the purge and installed 352.

Thanks all !!!

):P

[img]http://i.imgur.com/0sgcHhx.png[/img]

oldfred, it's practically an honour to get a reply from you, thanks for the informative one

---

