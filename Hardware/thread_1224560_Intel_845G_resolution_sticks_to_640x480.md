---
title: "Intel 845G: resolution sticks to 640x480"
date: 2009-07-27
forum: Hardware
---

### Post by mavio on 2009-07-27
Hi all! I'm not english so forgive grammar errors please :)
I managed to install Ubuntu 8.10 in a dual-boot configuration with Win XP on an old (bought in 2003) Dell Dimension 2400 (upgraded to 512 Mb RAM).
The problem is that I cannot set any resolution that isn't 640x480, i suspect due to the infamous Intel 845G integrated graphics chip installed into the PC.
I installed two times "xserver-xorg-intel-video" packet with apt-get, but, if someone claims it solves the problem, not for me.
My xorg.conf is very generic, I cannot post it right now because I'm away from that machine.
Reading through other posts, i tried a command like "sudo dpkg-configure -phigh xserver-xorg". Nothing happened, a backup file was automatically created with time and date appended. I am a novice to Linux and I can't understand what these commands do, I would be happy if you give me some hint.
Since I care my installation, because the most difficult part was setting WinXP bootloader to start Grub and then Ubuntu, I decided not to mess up things by copying random xorg.confs from the net, instead I would like some help from you.
Thanks

---

### Post by mavio on 2009-07-28
No reply?
:(

---

### Post by mavio on 2009-07-29
Updated to 9.04, nothing changes.

---

### Post by Moiman on 2009-08-02
Change shared Video Memory from 1MB to 8MB in BIOS

---

