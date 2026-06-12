---
title: "Problems with GRUB and swap files"
date: 2008-08-25
forum: Hardware
---

### Post by LOT7V on 2008-08-25
Hey all

I have an Acer TravelMate 4202WLMi laptop, and recently installed Linux onto an external hard drive.

My laptop was initially run by Windows.

It had a C: and D: drive.

During the install, I accidentally set the entire D: drive as the swap file, now it is gone and I want it back :-P.

So my first question is: how can I recover my D: drive?

Secondly, every time I start the laptop up WITHOUT the external being connected, it displays:
    GRUB loading, please wait...
    GRUB Error 21

My second question is: can I dual-boot without having GRUB installed?

My third question is: how can I remove GRUB or be able to use Windows without the external?

Any help will be much appreciated.

Thanks
LOT7V

---

### Post by logos34 on 2008-08-25
Try [TestDisk]("http://www.google.com/url?q=http://www.cgsecurity.org/wiki/TestDisk&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNEjaBPMpLTHfYngXkZgAt91p3mh_Q") to recover D: drive.

sudo apt-get install testdisk

sudo testdisk


Assuming your laptop Bios supports USB boot:

- Install grub to the MBR of the external hard disk

sudo grub-install /dev/sdb

gksudo gedit /boot/grub/menu.lst

-change 'groot' and 'root' lines to (hd**0**,?)

Make a new swap on the external:

sudo gparted

edit /etc/fstab to match

Restore windows bootloader using windows install cd (>recovery console>**fixmbr**) or _Super Grub Disk_ (see link my signature).

Then simply enter the Bios to toggle boot drive for OS of choice.

---

