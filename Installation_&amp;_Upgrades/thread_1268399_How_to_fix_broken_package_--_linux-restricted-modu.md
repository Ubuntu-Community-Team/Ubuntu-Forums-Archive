---
title: "How to fix broken package -- linux-restricted-modules-2.6.28.15-generic"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by nkao on 2009-09-16
Hi,
I am new to Linux / ubuntu and I want to install my first Linux machine.  This machine already has Windows XP running and I want to add Linux to it.

I downloaded the latest 9.04 CD from Ubuntu website and burned this image file to a CD.

Then I went through the demo and then I choose an old 160G IDE hard drive to install Linux.

After installed the OS, I found broken package "linux-restriced-modules-2.6.28.15-generic" from "Synaptic Package Manager".  Based on the description in "Synaptic Package Manager", I tried to install the "linux-restricted-modules-generic" meta-package with the command "sudo apt-get -f install" and the installation stopped due to an error occurred.

I am copying the output for your reference and please help to resolve this issue.  Thanks.

====================================================
norman@norman-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.28-15-generic
Suggested packages:
  fdutils linux-doc-2.6.28 linux-source-2.6.28
The following NEW packages will be installed:
  linux-image-2.6.28-15-generic
0 upgraded, 1 newly installed, 0 to remove and 219 not upgraded.
1 not fully installed or removed.
Need to get 0B/24.6MB of archives.
After this operation, 95.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 102649 files and directories currently installed.)
Unpacking linux-image-2.6.28-15-generic (from .../linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-mia.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

[B]Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
norman@norman-desktop:~$ 

====================================================

---

### Post by markusf21 on 2009-09-16
Are you sure your HD isn't full? one of the errors said that you don't have enough space.

---

### Post by nkao on 2009-09-16
Hi, 
I choose to install the Linux system onto a 160G hard drive which I already clean up the data.  But it seems that the installation only allocate 2.3GB for Linux and the root folder (2.1G) is already full.

How can I fully utilize the 160G HD space to make the new system running smoothly?

Appreciate for your input.

Norman

---

### Post by nkao on 2009-09-17
The space limitation issue was gone when I re-install the OS and select to use the entire disk space (160G) for the new system.

Thanks for all your attentions.

---

### Post by stlsaint on 2009-09-17
the default size of 2gb is a issue that is being handled with via launchpad...meantime i see you solved issue...if you dont care for personal customization of partitions you should be alright from here on.

---

### Post by nkao on 2009-09-17
Thanks for the comments.  I sure will come back to learn how to customize the HD space but I think that there more points that I want to explore first.

Cheers!

---

