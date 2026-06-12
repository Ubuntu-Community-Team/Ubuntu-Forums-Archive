---
title: "/usr/src/linux-*"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by Doug McKee on 2007-06-21
Hi all,

I've recently installed kubuntu 7.04 on my Thinkpad x60s and I want to rebuild the kernel with some of the config options suggested at thinkwiki.com ([http://www.thinkwiki.org/wiki/How_to_make_ACPI_work](http://www.thinkwiki.org/wiki/How_to_make_ACPI_work)).  My plan is to copy the existing kernel source from /usr/src, reconfigure it, and then install it from there using what I've learned from the O'Reilly book _Linux Kernel in a Nutshell_.  My installation is up to date and I'm running the 2.6.20-16 kernel, but I have two src directories:

   /usr/src/linux-headers-2.6.20-16
   /usr/src/linux-headers-2.6.20-16-generic

I'm pretty sure, based on what's in my /boot/grub/menu.lst, that I'm running the generic version, but does anyone know what the difference is between these two directories?  The generic directory is mostly symlinks into the other directory, so I'm thinking I'll need to copy (with tar) both before I start monkeying around.

Any insight would be appreciated!

Thanks,

Doug

---

### Post by 5-HT on 2007-06-21
Hi, those directories are just the kernel headers. You'll need the full kernel source if you want to compile your own kernel.

```
sudo aptitude install linux-source-2.6.20
```Also, there are some Debian-specific ways to automate kernel and module compilation and installation that may not be mentioned in Linux Kernel in a Nutshell (such as 'make-kpgk'). You may want to look [HERE ]("http://ubuntuforums.org/showthread.php?t=311158")for some of the differences. You can use the traditional way to compile the kernel, but these Debian (and therefore Ubuntu) tools can make things a lot easier and generate .debs for you automatically.

It'll show up in /usr/src.
cheers,

---

### Post by 5-HT on 2007-06-21
Duplicate post

---

### Post by IntuitiveNipple on 2007-06-21
Here are the essential steps:
```
$ cd /usr/src
$ sudo apt-get kernel-package fakeroot build-essential
$ sudo apt-get install linux-source
$ tar xjvf linux-source-A.B.C.D-EEEE.bz2
$ cp /boot/config-`uname -r` ./linux-source-A.B.C.D-EEEE/.config
$ cd linux-source-A.B.C.D-EEEE
$ make menuconfig
$ make-kpkg clean
$ fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 
$ cd /usr/src
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
$ sudo dpkg -i linux-image-A.B.C.D-EEEE-custom_A.B.C.D-EEEE-custom_i386.deb
$ sudo dpkg -i linux-headers-A.B.C.D-EEEE-custom_A.B.C.D-EEEE-custom-_i386.deb

```
You will need to specify the **tar** and  **dpkg** lines to match your kernel version file-names. I've used A.B.C.D-EEEE to represent them.

**make menuconfig** runs the kernel configuration utility. You can of course manually edit the ./config file instead using any text editor.

Make sure and back up the grub menu each time, and ***check it*** after you've installed the packages because, in Feisty at least, it is notorious for setting the wrong root partition (usually as a UUID) when you've got multiple root partitions on a  disk.

I always compare the UUID with that of the root partition I want each kernel listed in menu.lst to start with using:
```
$ ls -l /dev/disk/by-uuid
```

---

### Post by Doug McKee on 2007-06-26
OK, I'm back-- 

Thanks very much for your help!  I've been able to make some decent forward progress, but I'm not there yet. I followed the steps suggested by IntNip, and successfully rebuilt, reconfigured, and rebooted the machine.  I turned on the ACPI options that I wanted and they're not totally working, but the machine has not hung on waking up from sleep like it used to.  The lockscreen key doesn't work, but I've got some ideas for how to figure that out.

The show stopper is that wireless networking no longer shows up under KNetworkManager.  So clearly something (besides the new ACPI options) is different between my old precompiled kernel and my freshly compiled one.  It's a pretty standard Intel PRO/Wireless 3945ABG built in card (in a Lenovo x60s), so I'm kind of surprised it's not working now.

Any suggestions would be much appreciated!

Doug

---

