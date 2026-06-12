---
title: "HOWTO: Install Xubuntu on Toshiba Portege 3110CT with PXE"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by mic159 on 2009-04-16
This is my first HOW-TO, so take it easy on me :P

I wrote this because when googling, i could only find people who had the external CD drive for the laptop, and upgraded ram.
Where as i did not want to pay for out-dated ram and an external CD drive that i could only use on a crappy old system.

It took me a while but I finally worked out how to get Xubuntu/ubuntu on them (no X, just command line, but ubuntu none the less).

From much trial and error, I finally worked out that Xubuntu 6.06.1 is the version to go for. Because normal ubuntu wont recognize the harddrive, and Xubuntu has low memory mode when installing. Newer versions of Xubuntu dropped the low memory mode and hang when installing the locale, if it even gets that far.

Because it has no CD-ROM drive you will have to TFTP the network installer to it.

I ran TFTPD32 on the other 3110CT i had, but it will work with any windows computer. If you prefer to do it with linux, im sure you are resourceful enough to find an alternative.

TFTPD32 turns windows into a DHCP server and a TFTP server. So connect the two computers together with a crossover patch cable, or hook them both up to a switch that isnt connected to a router or anything with another DHCP server.

Download the Xubuntu 6.06.1 alternate ISO and copy the contents of the /install/netboot/ubuntu-installer/i386/ folder to the root of your TFTP serve directory.

Then open /pxelinux.cfg/default with a text editor and remove all refrences to "/ubuntu-installer/i386/" (ie. change "kernel ubuntu-installer/i386/linux" to "kernel linux", etc)

do the same in the /boot-screens/boot.txt if you want the pretty picture to work.

The computer running TFTPD32 must have a static IP set for the interface you will be running TFTPD32 on.
In the settings of TFTPD32 you want to enable "PXE Compatibility" and "Translate Unix file names" (not sure if this one is needed, but just in case)
Also make sure TFTP server and DHCP Server is enabled.
In the DHCP server tab, set the "Boot File" to "\pxelinux.0" and Default Router to the server's static IP.

Make sure they are connected via the ethernet.

Go into the BIOS of the 3110CT (hold esc while it starts, then press F1)
change the boot priority to say LAN first.
Save and restart.

It will boot off the TFTP server, and hopefully you will get a prompt asking you what install you want to do.
Type "server" and press enter. This will make it install the base system without X or a desktop manager. X wont run well (if at all) because it dosnt have much ram.
You can probably install it after you have it all up and running if you want to try it out.

After it finishes downloading the initrd.gz and linux (the part with all the dots), unplug it from the TFTP server and onto your normal lan with an internet connection.

I decided this was better than using the contents of the alternate CD in a web server, because often that would fail when choosing a kernel.

When it gets to the section asking you about which mirror you want to install from, choose your local mirror. I live in Australia, so i chose my ISP's mirror, because it dosnt count to your monthly quota, and its the fastest one for me (mirror.files.bigpond.com).

After it has finished installing, you will want to upgrade to the latest version of ubuntu.

This will have to be done in 2 stages, as 6.06 does not let you update directly to the latest (as far as i could see)
So we will have to upgrade to the latest LTS, then to the latest version.

To do this, install update-manager-core
```
sudo apt-get install update-manager-core
```
then
```
sudo do-release-upgrade
```

that should take a while, and might error about out of memory, but it still worked for me anyway.
Also, fsck took ages after it rebooted, but it got there in the end, so be patient.

when its all done, you will want to upgrade to the latest, now go in and
edit /etc/update-manager/release-upgrades and set
```
Prompt=normal
```
This file did not exist in 6.06, so we couldnt do this back then.
Then do:
```
sudo do-release-upgrade
```


If the system wont boot after installing the new kernels,
edit /boot/grub/menu.list
and change /dev/hda1 to /dev/sda1 on the new kernel because for some reason the naming changed for the new kernel (no need to change the old kernel)
But when I did this the second time it had changed them to /by-uuid/ automatically, so I didn't have this problem.

You should now have a nice little up to date ubuntu server. Now go and install whatever you want :)

If you want to use the full resolution of the screen, edit menu.list
and append vga=0x314 to make the console use 800x600 :D

EDIT:
If you notice, when updating to the latest version, it says /etc/kernel-img.conf needs to be updated, so here is what you need to change:

> ,----[ /etc/kernel-img.conf ]
| ...
| postinst_hook = /sbin/update-grub
| postrm_hook = /sbin/update-grub
`----

Should be change to:

,----[ /etc/kernel-img.conf ]
| ...
| postinst_hook = /usr/sbin/update-grub
| postrm_hook = /usr/sbin/update-grub
`----
(Nice snipit taken from ubuntuforums.org/showthread.php?t=644961)

---

