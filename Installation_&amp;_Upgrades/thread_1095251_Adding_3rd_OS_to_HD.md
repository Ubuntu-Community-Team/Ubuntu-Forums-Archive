---
title: "Adding 3rd OS to HD"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2009-03-13
1. Prior to present inability to boot I had XP and 8.10 on a boot sequence that was working quite well.
2. Attempted to install Debian, went through entire process and at boot the message was Boot From CD
Missing operating system
3.Using gparted CD determined all 3 OS were there. Debian had created an additional swap and an extended
Having no clue as to what to do and havig no access to another unit (I am next door at neighbor) I went on to #4) Could I have removed external, booted to XP and got help?
4. Using gparted I deleted everything from my external drive (both linux OS)
and repartitioned my 160GB HD in the following
I split the drive in half, created a swap with the intention of trying one more time. I merely want ubuntu 8.10 and debian on the external with a choice to boot to either of the 3.
5. Installed debian again to largest amt unallocated it installed, created an extended and a swap of its own.
6. At boot I am getting same error Boot from CD missing operating system.
So here I am waiting at a neighbors house for a solution and the only thought I have is maybe I should not originally choose to install grub in MBR.
Please someone help

---

### Post by maybeway36 on 2009-03-13
Maybe you should just install Ubuntu's GRUB. Either:
1. install Ubuntu after Debian, or
2. reinstall Ubuntu's GRUB from the CD. There are how-tos on this, but it varies a bit by situation.
3. Super Grub Disk is also a good option. Check it out.

---

