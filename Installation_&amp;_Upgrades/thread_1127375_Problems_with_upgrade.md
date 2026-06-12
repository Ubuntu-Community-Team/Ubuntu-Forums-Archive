---
title: "Problems with upgrade"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by pg159 on 2009-04-16
I'm a complete Linux/Ubuntu novice interested in exploring the OS. Decided to do that by installing a virtual Ubuntu machine on my MacBook Pro under Parallels Desktop 3.0. The original installation went smoothly and everything was running great. 

Shortly afterwards, the update icon appeared with a long list of recommended updates. I ran this and afterwards the system behaved normally. The next time I tried to start the Ubuntu VM it failed with the following message.

_______________

Starting up ...
[ 971.188264] ACPI: Unable to load the System Description Tables
Loading, please wait ...
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules is /dev
ALERT! /dev/disk/by-uuid/2b791d3e-905c-4a23-9e4f-6e3e53177daf does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
_______________


If I hit [esc] on the Grub screen, I get the following choices:

Ubuntu 8.04.2, kernal 2.6.24-23-generic
Ubuntu 8.04.2, kernal 2.6.24-23-generic (recovery mode)
Ubuntu 8.04.2, kernal 2.6.24-19-generic
Ubuntu 8.04.2, kernal 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.2, memtest86+

I tried selecting each of the four kernals, all gave the same error as before. For the heck of it, I also tried the last one. It started a test routine which my system passed.

I posted this and RomeReactor suggested that I look at this thread:  [http://ubuntuforums.org/showthread.php?t=987243](http://ubuntuforums.org/showthread.php?t=987243)

_______________

How about when you get the Grub menu on start up, select the first Ubuntu kernel entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add "rootdelay=130" similar to:
Code:
kernel	/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash rootdelay=130
Press enter to save the change, then "b" to boot. Let me know if that makes any difference. 

_______________

I tried this, even tried different delay times, no change. At that point, I gave up, trashed the VM files and started over. Once I had a working Ubuntu VM, I made a backup copy of it just in case. I then used it for the past two months without upgrading and all was fine except for large arrow telling me that there were upgrades available. Finally, I decided to try upgrading again (on a copy of the VM).

All went well except that one file "tzdata" (time zones and daylight savings time) could not be fetched. I got an error "could not resolve us.archive.ubuntu.com". After the upgrade, all was fine until I restarted. Then I got the exact same behavior as before.

I decided to start both the original and the upgraded copies and hit [esc] so that I could inspect the kernel lines.

    Original VM    -    kernel/boot/vmlinuz-2.26.24-23-generic root=UUID=413a4b7b-2f56-48f7-925e-f97f2720ff0a ro quiet splash vga=791

    Upgraded VM -    kernel/boot/vmlinuz-2.26.24-23-generic root=UUID=2b791d3e-905c-4a23-9e4f-6e3e53177daf ro quiet splash

I appended vga=791 to the upgraded version and booted => no change.
I replaced 2b791d3e-905c-4a23-9e4f-6e3e53177daf with 413a4b7b-2f56-48f7-925e-f97f2720ff0a and appended vga=791 in the upgraded version and IT WORKED until I restarted. Then it behaved just as before and when I inspected the kernel line, it was still "...2b79.......splash"

I repeated the above edit, got it working and inspected /proc/cmdline and the /dev/disk/by-UUID folder. cat cmdline returns "root=UUID=413a4b7b-2f56-48f7-925e-f97f2720ff0a ro quiet splash vga=791". The by-UUID folder contains three files, of type "link to block device":

   413a4b7b-2f56-48f7-925e-f97f2720ff0a    which points to sda1
   9a208a96-dafc-49c9-938d-e80704749182  which points to sdb1
   0464c93f-2bca-4bce-998f-2ab4a1cc793f which points to sdc1

I logged in as root and tried renaming the file 413a4b7b-2f56-48f7-925e-f97f2720ff0a to 2b791d3e-905c-4a23-9e4f-6e3e53177. Restarted and got the exact same behavior as before 

_________

ALERT! /dev/disk/by-uuid/2b791d3e-905c-4a23-9e4f-6e3e53177daf does not exist.
_________

I have no idea what to try next. Editing the kernel every time I restart is a pain in the a**. Do I just live with the original system and ignore its messages to upgrade? Any ideas?

---

### Post by pg159 on 2009-04-21
This is the second time I've posted about problems after upgrading Ubuntu. Both times, I got lots of readers but, so far, only one reply. I'm out of ideas. Isn't there anyone in this forum with a suggestion?

Ubuntu looks interesting but my impression, based on this, is that it is very fragile, not very robust.

---

### Post by Partyboi2 on 2009-04-22
Check your /etc/fstab that it has the correct UUID listed, ```
gksu gedit /etc/fstab
``` if it does not then backup your current /etc/fstab 
```
sudo cp /etc/fstab /etc/fstab.old
```and make the changes.

---

### Post by pg159 on 2009-04-22
Partyboi2,

Thanks for the answer. I was beginning to think no one was here.

It looks like /etc/fstab has the correct UUID listed:

______
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=413a4b7b-2f56-48f7-925e-f97f2720ff0a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=0464c93f-2bca-4bce-998f-2ab4a1cc793f /home           xfs     relatime        0       2
# /dev/sdb1
UUID=9a208a96-dafc-49c9-938d-e80704749182 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
________

As you've probably guessed, I'm not a hard-core Unix user. It seems that during startup the system is looking for the wrong UUID file but both /etc/fstab and /proc/cmdline point to the correct UUID. Why won't the change I made to the kernel stick? 

One OT question. How do you format your forum posts so that your code shows up in the smaller boxes? Sure makes it easier to read.

---

### Post by Partyboi2 on 2009-04-22
To add the code box highlight the text that you want in the code box and press the **#** icon.

The only other thing I can think of is to check your /boot/grub/menu.lst that it has the correct uuid.
```
cat /boot/grub/menu.lst
```

---

### Post by pg159 on 2009-04-22
Partyboi2,

Thank you. Editing /boot/grub/menu.lst solved the problem. All is working again.

Of course, I now have the System Update arrow back telling me that there are 29 updates available! After this experience, I'm hesitant to follow the system's advice.

Thanks again for your help.

---

### Post by transformation on 2009-04-24
> **pg159 said:**
> Partyboi2,

Thank you. Editing /boot/grub/menu.lst solved the problem. All is working again.

Of course, I now have the System Update arrow back telling me that there are 29 updates available! After this experience, I'm hesitant to follow the system's advice.

Thanks again for your help.

pg159 can you tell me how you fixed the problem??.. I've ran into the same problem you had.. can you please tell me how you solved the problem. thanks in advance

---

### Post by pg159 on 2009-04-27
Transformation,

Do you also have Ubuntu running as a VM under Parallels? If so, I can reiterate each of the steps that solved my problem. If you have a non-VM installation, I have no idea where to begin.

---

