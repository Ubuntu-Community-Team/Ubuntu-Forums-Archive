---
title: "GRUB(2) trouble in 9.10 installation"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Fleuris on 2009-10-29
Hello,

I just installed Windows 7 and Ubuntu 9.10, but I immediatly get the most annoying problem ever: I have no GRUB! #-o Yes, I selected 'Install boot manager'. I've read somewhere that GRUB2 would not replace another bootloader, but I want it to replace the Win7 loader!!!

What can i do to get GRUB2? (Or the normal GRUB if thats nessecary) Reinstalling or formatting is no problem, as I haven't really installed things yet.

---

### Post by VMC on 2009-10-29
Follow this [guide]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html").

---

### Post by Fleuris on 2009-10-30
> **VMC said:**
> Follow this [guide]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html").

Thanks for the reply, but I can't get past the 'fdisk -l'  part, because fdisk says he's unable to aquire a list of devices. I've tried all possible fdisk commands, but nothing works.

Btw, I have 2x 500GB in Raid0 with a Intel ICH10 (X58 ) Chipset.

---

### Post by Fleuris on 2009-10-30
No answer......... So, I've tried something myself. I've tried all mounting, fdisk and grub commands that I know. But I haven't got a single step further. I've figured out that my raid is named: /dev/mapper/isw_cbjhjehefd_7200.12 (7200.12 is the name of my array) But when I try to mount it, it gives an error syaing that is is already mounted, or /mnt is busy. When I mount the two partitions (win7 & ubuntu) with nautilus, and I try to install grub. It says grub-probe cant find a device for /boot/grub. I've tried all the evices/partition I have, but it keeps giving the same error. When I try to probe, it also gives an error, saying he can't anything (or something like that).

Please help guys! I know how to install GRUB, but Ubuntu/grub won't accept my Raid0 array as device, nor the existing partitions. I'm a bit in a hurry with this...

---

### Post by DUCKFACE on 2009-10-30
Same here 
i have raid0. on clean instalation its visible .. partitions are made .. BUT .. when i got to the point that GRUB must be installed.... it failed on 16% and kiked me oput in to ubuntu server installer main menu. any ideas how to fix this ?

---

### Post by DUCKFACE on 2009-10-31
Solved: clean install on 8.10 and after taht do-release-upgrade to 9.10 :)

---

### Post by Fleuris on 2009-10-31
> **DUCKFACE said:**
> Solved: clean install on 8.10 and after taht do-release-upgrade to 9.10 :)

But do you have GRUB2 then? Anyway, I'll try it! :)

---

### Post by rkolb86 on 2009-10-31
Somewhat Related....

I used the 9.10 Alt CD on my machine with ICH10 Raid 1 (Mirrored).

Installed Ubuntu to another drive (not RAID, the RAID array is just file storage)

Upon installing, it asked if I wanted to use the RAID hardware...I said yes.

after installing, Ubuntu sees my 2 storage drives as separate drives.

Worked fine with 8.04. Odd

---

### Post by cgb223 on 2009-11-04
same problem as duckface down to the percent with raid0 using dmraid and the alt install (naturally). did anyone write a bug report to the grub people or is it solved? 

Thanks in advanced

---

### Post by hotweiss on 2009-11-05
This is driving me crazy!

---

### Post by chiisama on 2009-11-07
same problem here with ich10 raid(1) with lvm - grub fails to install (at boot there always comes this "grub error")
the only thing i found about this in the bugtracker is [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340) - but it seems to be fixed

does anyone know more about this? is it already reported?

---

### Post by kevpatts on 2009-11-09
> **rkolb86 said:**
> Somewhat Related....

I used the 9.10 Alt CD on my machine with ICH10 Raid 1 (Mirrored).

Installed Ubuntu to another drive (not RAID, the RAID array is just file storage)

Upon installing, it asked if I wanted to use the RAID hardware...I said yes.

after installing, Ubuntu sees my 2 storage drives as separate drives.

Worked fine with 8.04. Odd
Sounds like you have a fakeraid setup and therefore do not have any RAID **hardware**. Fakeraid and hardware RAID are two very different things.

---

