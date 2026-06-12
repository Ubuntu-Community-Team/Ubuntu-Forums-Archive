---
title: "Help during install nothing but command prompt appears"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by mxboy15u on 2009-04-09
On a co-workers computer we are trying to install Ubuntu to a fresh hard drive, it installs a little and then just stalls and shows a command line with black screen.

---

### Post by mxboy15u on 2009-04-09
(  0.00000) ACPI:DMI BIOS year =0, assuming ACPI-capable machine loading, please wait......


Busybox v1.10.2 (Ubuntu 1:.10.2-1ubuntu6) built in shell (ash) Enter "help" for a list of built-in commands

These are the messages he is getting.

---

### Post by upchucky on 2009-04-09
does the live ubuntu cd boot to a graphical desktop? if yes then busybox is waiting for the commands from you to set up grub.


if you get to a graphical desktop when you boot with the live cd then

download this,

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh

```

post the results of this file here, it will contain the drive geometry of what is on the drive and provide information need to get grub working.

with this information grub can be set up using supergrub to setup/repair grub.

get super grub here,

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk, boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

---

### Post by mxboy15u on 2009-04-09
Unfortunately it cannot boot into a live desktop off of the CD either.

Can this install really be this complicated? What causes this?

---

### Post by TBerk on 2009-04-09
> **mxboy15u said:**
> On a co-workers computer we are trying to install Ubuntu to a fresh hard drive, it installs a little and then just stalls and shows a command line with black screen.

What version of Ubuntu is the boot/install CD?


TBerk

---

### Post by mxboy15u on 2009-04-09
He tried 8.10 and 9.04

---

