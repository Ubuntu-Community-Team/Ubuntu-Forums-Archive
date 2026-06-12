---
title: "Mounting an .iso and installing on another partition"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by Lord Butters I on 2009-07-28
Is it in any way possible to install an OS onto a blank partition from within Ubuntu?  I have two primary partitions on my laptop, one with ubuntu but one that I need Windows on.  I downloaded the Windows 7 Release Candidate, but I don't want to have to buy a DVD if it can be avoided.  Can I do something that will allow me to install Windows 7 onto my blank partition without burning it to disk?

---

### Post by fouserge on 2009-07-28
I'm not sure how but if you have a usb drive you should be able to make it bootable with a disc image. I think Jaunty may have a tool already there for you to do it with but I'm not sure.

---

### Post by stlsaint on 2009-07-29
well to the poster unless you try the live usb creator built into ubuntu (fouserge:) than no you cannot...from what i know...install any os from inside and other os without doing a virtual machine! actually it would be in your best interest to install from a disc onto your new partition and when you restart you will automatically load windows...then from there get a bootloader program...i like "easybcd" and point your bootloader to both your partitions(look up instructions before doing this part!) i have done it many-a-times and i now run winxp, vista and ubuntu on one machine thru partitions! after you point the bootloader to see your windows partition and your ubuntu partition you will have the option of which one to boot from at the boot screen every restart!! DONT FORGET TO RE-INSTALL THE VISTA MBR IN EASYBCD AS WELL OR WHATEVER PROGRAM YOU DECIDE TO USE!!

please seek more help if needed!!!

---

### Post by vinutux on 2009-07-29
Try **Virtualbox** install another os in your current platform...

---

### Post by Mark Phelps on 2009-07-29
> **Lord Butters I said:**
> ... Can I do something that will allow me to install Windows 7 onto my blank partition without burning it to disk?

While you can certainly mount the ISO in Ubuntu, the problem then will be that you will need to be able to run the setup.exe program -- which is an MS Windows executable and will not run in Linux.

The load-ISO-to-USB-and-run options for installing Ubuntu work because they run Linux programs, not MS Windows programs.

---

### Post by m-p{3} on 2009-07-29
With GRUB2 you theorically could boot an ISO directly, but I haven't found a way of booting a non-linux bootable ISO file.

---

### Post by Lord Butters I on 2009-07-31
> **Mark Phelps said:**
> While you can certainly mount the ISO in Ubuntu, the problem then will be that you will need to be able to run the setup.exe program -- which is an MS Windows executable and will not run in Linux.


Now this I do not understand.  With Wine I can run setup.exe programs from things like game installations, but with my Windows 7 .iso it shows up as empty, even when I reveal hidden files.  It's not; when I load it up in Virtualbox it works fine, but Vbox won't work; I need every bit of ram I have to have a hope of running the applications I need.

---

