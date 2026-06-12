---
title: "GRUB, different disks and windows"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by lorenzov on 2008-12-04
hello everyone,

i've got a newby question, but even with some research i can't get it to work...


i've got a machine with 4 hard disks installed; the master has windows 2003 server on. here is the list of things from gpart:

/dev/sda1    ntfs 240gb (little free space, no not allocated space, flagged as boot?)
/dev/sdb1    ntfs 74gb  (BOOT, 8mb unallocated*)
/dev/sdc1    ntfs 300gb (no unallocated)

disk 4
/dev/sdd1    ext3        149gb
/dev/sdd2    extended    2.88gb
/dev/sdd5    linux-swap  2.88gb

*please note:
i installed the latest version on the completely unpartitioned space of disk 4 and allocated sdb1 (boot for GRUB), however the machine did not boot at all getting stuck when grub loaded.
the above is the result of the guided install; to get it back i run fixmbr and at least be able to run windows again which i think left the partition with 8mb unallocated.

does anyone has any suggestion on what did i do wrong? 
one thing which is puzzling me is why sda1 is flagged as boot...
thanks for your suggestions!

---

### Post by caljohnsmith on 2008-12-04
Can you set your BIOS to boot the Ubuntu drive on start up? If so, that is probably the most ideal solution for your situation; you can then install Grub to the MBR of the Ubuntu drive to make it bootable. Just open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> root (hd3,0)
grub> setup (hd3)
grub> quit
```
Please post the output of the above commands, reboot, set you BIOS to boot the Ubuntu drive, and you should at least get the Grub menu on start up. Let me know if you get that far or if you run into problems. :)

---

### Post by lorenzov on 2008-12-04
thanks for the reply, unfortunately no, trying to change the bios boot device is just leading to a blank screen with no boot. evidently there is something wrong with the grub default settings during the installation when you try to use a different disk (or one that doesn't have a mbr on it)...

will try to wipe and reinstall, but with a slow computer is not really pleasant!

---

### Post by lorenzov on 2008-12-05
what a nightmare! after a lot of fiddling i got it to work...well, somehow.

the reply from caljohnsmith put me in the right direction, however i had to go and digg a bit more in the forum to figure out that nearly everyone trying to install ubuntu on a second drive, let alone with the mix of ide and sata as i have, is having some boot problems. 

i hope that someone who is not a newby like me will be able to feed this back in the grub development.

as far as my solution goes, it looks like that the mapping of the drives from the live cd doesn't really match with the bios/startup. so, if you run the 

find /boot/grub/stage1 from the live cd i would get hd3,0

what happened to me, however, is that when the guided installation is doing the work, it install grub in the root of hd3, rather as one might expect, on the real hd0 which contains the mbr for windows.

if you select the boot device manually, and get the disk with ubuntu on, finally the grub menu comes up, however, at this point, you will get an error 17, because if you run again  

find /boot/grub/stage1 
this time i get hd0,0

the only way to run ubuntu, then, is to change the root manually from hd3,0 to hd0,0 and then boot.

is there anyone who could suggest how could i make this change permanent? 

i had a quick look at the menu.lst file, but i'd rather not mess with it without knowing what i'm doing given that it took me a day to figure out how to start!

thanks!

---

### Post by caljohnsmith on 2008-12-05
You're absolutely right in that Grub sees the order of HDDs differently on start up compared to how Grub sees the drives when you are in Ubuntu. On start up, Grub sees the order of drives the same as the BIOS boot order:
```
(hd0) = 1st boot drive (1st drive in the BIOS boot order)
(hd1) = 2nd boot drive (2nd drive in the BIOS boot order)
(hd2) = 3rd boot drive (3rd drive in the BIOS boot order)
...etc.
```
So if you set your BIOS to boot the Ubuntu sdd drive, then Grub sees the sdd drive as (hd0) on start up; that's why you had to modify your Ubuntu entries to use (hd0,0) instead of (hd3,0). But when you are in Ubuntu, Grub sees the order of drives the same as they are ordered /dev, i.e. the drives are ordered by whether they are IDE, SATA, USB, etc, so the following is true when you use Grub commands in Ubuntu:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc.
```
So anyway, if you want to update your menu.lst so that your Ubuntu entries use (hd0,0) instead of (hd3,0), first open it with:
```
gksudo gedit /boot/grub/menu.lst
```
And then change all the Ubuntu entries similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
[COLOR="Blue"]root            (hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```
Also make sure to change the "groot" line:
```
# groot=(hd0,0)
```
And then you should be all set. :)

---

