---
title: "trying to install on nslu2"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by jrosw on 2009-08-01
I am trying to install on an nslu2 using the information in the wiki at [https://wiki.edubuntu.org/ARM/NSLU2](https://wiki.edubuntu.org/ARM/NSLU2)

I've got the NSLU2 booted, and can connect via ssh and access the installer. The problem is that as soon as the install gets to the "detecting hardware" phase the ssh connection is terminated and I can go no further. A reboot is then required to access the installer again, as reconnecting and selecting "start installer" simply returns to the "detecting hardware" and disconnects again.

Anyone know a way to get past this? Or an alternate way of installing Ubuntu on a nslu2?

Thanks for any help.

edit: I was able to get past the hardware detection by using advanced installation and hitting the Go Back option twice when asked to partition.. However the base installation fails and produces the following log entries. I selected to include only drivers required for this system when asked, so now I'm trying the generic option. However I'm not optimistic about that working.

**edit: ** That didn't work :( I also found the entry in the main Ubuntu wiki for this ([https://wiki.ubuntu.com/ARM/NSLU2](https://wiki.ubuntu.com/ARM/NSLU2)), however it links to the same installer as the page linked above, so no help there. So I am at a complete loss on how to get this working. I am now trying for the second time to install Debian using the guide on NSLU2-Linux.org. The first time I tried that, the install succeeded only to reboot into an install with no networking and no power light. I did have an earlier version of Debian on there so I KNOW this should work...

Here is the Ubuntu log:

Jan  1 01:18:16 in-target: The following extra packages will be installed:
Jan  1 01:18:16 in-target:   linux-firmware linux-image-2.6.28-14-ixp4xx wireless-crda
Jan  1 01:18:16 in-target: Suggested packages:
Jan  1 01:18:16 in-target:   fdutils linux-doc-2.6.28 linux-source-2.6.28
Jan  1 01:18:16 in-target: Recommended packages:
Jan  1 01:18:16 in-target:   flash-kernel
Jan  1 01:18:16 in-target: The following NEW packages will be installed:
Jan  1 01:18:16 in-target:   linux-firmware linux-image-2.6.28-14-ixp4xx linux-image-ixp4xx wireless-crda
Jan  1 01:18:18 in-target: 0 upgraded, 4 newly installed, 0 to remove and 18 not upgraded.
Jan  1 01:18:18 in-target: Need to get 10.5MB of archives.
Jan  1 01:18:18 in-target: After this operation, 29.7MB of additional disk space will be used.
Jan  1 01:18:18 in-target: Get:1 [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main wireless-crda 1.7 [16.5kB]
Jan  1 01:18:18 in-target: Get:2 [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty-updates/main linux-image-2.6.28-14-ixp4xx 2.6.28-14.47 [6706kB]
Jan  1 01:18:32 in-target: Get:3 [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main linux-firmware 1.11 [3737kB]
Jan  1 01:18:39 in-target: Get:4 [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty-updates/main linux-image-ixp4xx 2.6.28.14.19 [3518B]
Jan  1 01:18:58 in-target: Fetched 10.5MB in 22s (473kB/s)
Jan  1 01:18:59 in-target: tar:
Jan  1 01:18:59 in-target: ./md5sums: time stamp 2009-03-10 23:54:50 is 1236724550.673372953 s in the future
Jan  1 01:18:59 in-target:
Jan  1 01:18:59 in-target: tar:
Jan  1 01:18:59 in-target: ./control: time stamp 2009-03-10 23:54:50 is 1236724550.663545421 s in the future
Jan  1 01:18:59 in-target:
Jan  1 01:18:59 in-target: tar:
Jan  1 01:18:59 in-target: .: time stamp 2009-03-10 23:54:50 is 1236724550.656418421 s in the future
Jan  1 01:18:59 in-target:
Jan  1 01:18:59 in-target: Selecting previously deselected package wireless-crda.
Jan  1 01:18:59 in-target: (Reading database ...
Jan  1 01:19:00 in-target: 10575 files and directories currently installed.)
Jan  1 01:19:00 in-target: Unpacking wireless-crda (from .../wireless-crda_1.7_armel.deb) ...
Jan  1 01:19:06 in-target: tar: ./postrm: time stamp 2009-07-25 08:12:21 is 1248504794.935429564 s in the future
Jan  1 01:19:06 in-target: tar: ./postinst: time stamp 2009-07-25 08:12:21 is 1248504794.910421807 s in the future
Jan  1 01:19:06 in-target: tar: ./preinst: time stamp 2009-07-25 08:12:21 is 1248504794.903482079 s in the future
Jan  1 01:19:06 in-target: tar: ./control: time stamp 2009-07-25 08:15:24 is 1248504977.901234018 s in the future
Jan  1 01:19:06 in-target: tar: ./md5sums: time stamp 2009-07-25 08:15:26 is 1248504979.881460821 s in the future
Jan  1 01:19:06 in-target: tar: ./prerm: time stamp 2009-07-25 08:12:21 is 1248504794.878403229 s in the future
Jan  1 01:19:06 in-target: tar: .: time stamp 2009-07-25 08:15:24 is 1248504977.877245714 s in the future
Jan  1 01:19:06 in-target: Selecting previously deselected package linux-image-2.6.28-14-ixp4xx.
Jan  1 01:19:06 in-target: Unpacking linux-image-2.6.28-14-ixp4xx (from .../linux-image-2.6.28-14-ixp4xx_2.6.28-14.47_armel.deb) ...
Jan  1 01:19:19 debconf: Obsolete command TITLE Configuring linux-image-2.6.28-14-ixp4xx called
Jan  1 01:19:23 in-target: Done.
Jan  1 01:20:25 in-target: tar: ./md5sums: time stamp 2009-04-02 21:47:01 is 1238703995.895520762 s in the future
Jan  1 01:20:25 in-target: tar: ./control: time stamp 2009-04-02 21:47:00 is 1238703994.88848308 s in the future
Jan  1 01:20:25 in-target: tar: .: time stamp 2009-04-02 21:47:01 is 1238703995.887235489 s in the future
Jan  1 01:20:25 in-target: Selecting previously deselected package linux-firmware.
Jan  1 01:20:25 in-target: Unpacking linux-firmware (from .../linux-firmware_1.11_all.deb) ...
Jan  1 01:20:36 in-target: tar: ./md5sums: time stamp 2009-07-28 16:05:39 is 1248792302.884808139 s in the future
Jan  1 01:20:36 in-target: tar: ./control: time stamp 2009-07-28 16:05:22 is 1248792285.861680411 s in the future
Jan  1 01:20:36 in-target: tar: .: time stamp 2009-07-28 16:05:39 is 1248792302.860542411 s in the future
Jan  1 01:20:36 in-target: Selecting previously deselected package linux-image-ixp4xx.
Jan  1 01:20:36 in-target: Unpacking linux-image-ixp4xx (from .../linux-image-ixp4xx_2.6.28.14.19_armel.deb) ...
Jan  1 01:20:39 in-target: Setting up wireless-crda (1.7) ...
Jan  1 01:20:40 in-target: Setting up linux-image-2.6.28-14-ixp4xx (2.6.28-14.47) ...
Jan  1 01:20:42 in-target: Running depmod.
Jan  1 01:21:05 in-target: update-initramfs: Generating /boot/initrd.img-2.6.28-14-ixp4xx
Jan  1 01:21:07 in-target: readlink:
Jan  1 01:21:07 in-target: missing operand
Jan  1 01:21:07 in-target:
Jan  1 01:21:07 in-target: Try `readlink --help' for more information.
Jan  1 01:21:07 in-target: mkinitramfs: missing  root  /sys entry
Jan  1 01:21:07 in-target: mkinitramfs: workaround is MODULES=most
Jan  1 01:21:07 in-target: mkinitramfs: Error please report the bug
Jan  1 01:21:07 in-target: update-initramfs: failed for /boot/initrd.img-2.6.28-14-ixp4xx
Jan  1 01:21:07 in-target: Failed to create initrd image.
Jan  1 01:21:07 in-target: dpkg: error processing linux-image-2.6.28-14-ixp4xx (--configure):
Jan  1 01:21:07 in-target:  subprocess post-installation script returned error exit status 2
Jan  1 01:21:09 in-target: Setting up linux-firmware (1.11) ...
Jan  1 01:21:09 in-target: dpkg: dependency problems prevent configuration of linux-image-ixp4xx:
Jan  1 01:21:09 in-target:  linux-image-ixp4xx depends on linux-image-2.6.28-14-ixp4xx; however:
Jan  1 01:21:09 in-target:   Package linux-image-2.6.28-14-ixp4xx is not configured yet.
Jan  1 01:21:09 in-target: dpkg: error processing linux-image-ixp4xx (--configure):
Jan  1 01:21:09 in-target:  dependency problems - leaving unconfigured
Jan  1 01:21:09 in-target: No apport report written because the error message indicates its a followup error from a previous failure.
Jan  1 01:21:10 in-target: Errors were encountered while processing:
Jan  1 01:21:10 in-target:  linux-image-2.6.28-14-ixp4xx
Jan  1 01:21:10 in-target:  linux-image-ixp4xx
Jan  1 01:21:11 in-target: E:
Jan  1 01:21:11 in-target: Sub-process /usr/bin/dpkg returned an error code (1)
Jan  1 01:21:11 in-target:
Jan  1 01:21:14 base-installer: error: exiting on error base-installer/kernel/failed-install
Jan  1 01:21:30 main-menu[2193]: WARNING **: Configuring 'bootstrap-base' failed with error code 1
Jan  1 01:21:30 main-menu[2193]: WARNING **: Menu item 'bootstrap-base' failed.
Jan  1 01:21:45 main-menu[2193]: DEBUG: resolver (libgcc1): package doesn't exist (ignored)

Has anyone successfully got this working?

---

