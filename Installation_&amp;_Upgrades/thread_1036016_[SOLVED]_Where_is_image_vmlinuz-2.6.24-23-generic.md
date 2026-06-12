---
title: "[SOLVED] Where is image vmlinuz-2.6.24-23-generic ?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by eyanwube on 2009-01-10
Can someone tell me where I can download image vmlinuz-2.6.24-23-generic ?
My /boot got 100% full during an update and I deleted image vmlinuz-2.6.24-23-generic by mistake.  Now everytime I try any updates I get this message :
Internal Error: Could not find image (/boot/vmlinuz-2.6.24-23-generic)

TIA
Bernie

---

### Post by caljohnsmith on 2009-01-10
If you can still boot into Ubuntu OK using a different kernel, you could try the following in a terminal (Applications > Accessories > Terminal):
```
sudo apt-get purge linux-image-2.6.24-23-generic
sudo apt-get install linux-image-2.6.24-23-generic

```
Watch carefully what the purge command above says, because if it also uninstalls any other packages, like the linux modules for that kernel for example, you'll also need to reinstall that. But how about trying the above first and please post the output.

---

### Post by eyanwube on 2009-01-10
Thanks caljohnsmith.  
I think your suggestion worked.  Won't know for sure until the next upgrade comes along.  I am posting the output of the 2 commands you suggested :

wube@wube:~$ sudo apt-get purge linux-image-2.6.24-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-libvirt libxalan110 libvirt0 libxen3 python-gtk-vnc libxerces27 python-virtinst libntfs-3g23 python-urlgrabber
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-2.6.24-23-generic*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 61.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 219081 files and directories currently installed.)
Removing linux-image-2.6.24-23-generic ...
Running postrm hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-23-386
Found kernel: /vmlinuz-2.6.24-22-386
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.24-23-generic ...
Running postrm hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-23-386
Found kernel: /vmlinuz-2.6.24-22-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-23-generic': Directory not empty
wube@wube:~$ 

wube@wube:~$ sudo apt-get install linux-image-2.6.24-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-libvirt libxalan110 libvirt0 libxen3 python-gtk-vnc libxerces27 python-virtinst libntfs-3g23 python-urlgrabber
Use 'apt-get autoremove' to remove them.
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
  linux-image-2.6.24-23-generic
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/18.4MB of archives.
After this operation, 61.9MB of additional disk space will be used.
Selecting previously deselected package linux-image-2.6.24-23-generic.
(Reading database ... 216808 files and directories currently installed.)
Unpacking linux-image-2.6.24-23-generic (from .../linux-image-2.6.24-23-generic_2.6.24-23.46_i386.deb) ...
Done.
Setting up linux-image-2.6.24-23-generic (2.6.24-23.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-23-386
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-386
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done


wube@wube:~$

---

### Post by caljohnsmith on 2009-01-11
Looks like everything went smoothly, so if you have any more problems with it, let me know, but otherwise looks like you should be OK. :)

---

