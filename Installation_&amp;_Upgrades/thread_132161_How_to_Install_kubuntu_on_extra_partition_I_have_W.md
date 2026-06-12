---
title: "How to Install kubuntu on extra partition? I have WinXP+MDK2006 dual boot."
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by mexlinux on 2006-02-17
Hi:
I'm a Mandriva 2006.0 user, complaining about suspend functions.
My laptop Dell Inspiron 630m is reported to suspend correctly on ubuntu, so I want to try Kubuntu 5.10

I have been using linux for 4 years, but have never installed several distros on the same machine.

I already have a dual boot with Mandriva and WinXP,  I know that LILO is on the MBR (as far as I remember, how to know?), and I want to have kubuntu on an extra partition.

I already have this paritions on my disk:
sda1 Dell Utility
sda2 NTFS /mnt/widows
sda5 ext3 /
sda7 Linux swap
sda6 ext3 /home (with many available space)
sda3 CP/M / CTOS / .... (What the hell is that???)
and 7.8Mb empty space (I do not know why)

I have space on sda6, so I can resize to create new partitions, how many should I create? and of what type? Is it safe to share home and swap or should I create new versions?
Should I do it by hand from Mandriva? 
or will the kubuntu install program propose or will do those things for me?

What about LILO? will kubunto install a new one? or should I keep and modify from Mandriva?... In general how to control such things?

Is a network  connection required during installation?

...more questions to come....

Any help will be really appreciated!
Thanks
Miguel

---

### Post by wcks48 on 2006-02-17
i'm just cutious bout how to make my linux os see my third partition. i had 4 partition actually, the first is reserved for windows. all the three i just formatted through installation of Kubuntu. one is for root, one is swap, and one is for storage. but the storage partition can't even being detected by both window and linux. so i lost my third partition.... so sad. any solution for this?

---

### Post by mexlinux on 2006-02-18
Don't you have it in /etc/fstab?

---

