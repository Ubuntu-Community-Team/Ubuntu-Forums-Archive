---
title: "Another dual boot topic!"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by MadsRH on 2007-03-05
Hi
I know there's a lot of post's on this topic, but I can't find any clues to my problem.
Anyway, I'm trying to run both Ubuntu and XP on my PC. I the BIOS I've set the Ubuntu harddrive as 1. boot (although the jumpers are set as slave). This works fint, Ubuntu is running nicely from the slave harddrive, but I can't see the NTFS drive in Ubuntu or in the GRUB boot menu!

Can anyone tell me what to do?[B]
MadsRH[/B]

---

### Post by MadsRH on 2007-03-05
Is this the wrong categoric or why are there no one with just an idea? :confused: :confused:

---

### Post by eggdeng on 2007-03-05
You'll need to mount the XP partition in order to be able to see it. But first, a little more info would be useful. Type ```
df
``` in a terminal and post the output.

---

### Post by MadsRH on 2007-03-06
Thanks. Here it is:

Filsystem           1K-blokke     Brugt   Tilbage Brug% Monteret på
/dev/hdb1              9408480   3009888   5920660  34% /
varrun                  517828        84    517744   1% /var/run
varlock                 517828         4    517824   1% /var/lock
procbususb               10240       164     10076   2% /proc/bus/usb
udev                     10240       164     10076   2% /dev
devshm                  517828         0    517828   0% /dev/shm
lrm                     517828     18132    499696   4% /lib/modules/2.6.17-11-386/volatile
madsrh@madsrh-desktop:~$

---

