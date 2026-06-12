---
title: "Upgrade from 9.04 to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by kristapsl on 2009-10-30
Hi
I am newbie in the ubuntu. I am using dual boot (windows7 and ubuntu 9.04)
Yesterday, using upgrade manager, tried upgrade to ubuntu10. Downloaded packeges, install them, clean up and the ubuntu 9.04 asked to restart computer. After restart started problems- unable to boot ubuntu, (Monitor goes black , then sound ubuntu saound and nothing, just black screen all time)
When I tried reinstall ubuntu from CD, nothing again (except installation menu and choosing installation language, after that just black screen and cd room working and then stops.

Please help.

p.s. Sorry about my english

---

### Post by maxideci on 2009-10-30
Hi Kristapsl, 

try booting from live CD, I mean do not try to install ubuntu, but to run from the CD.

once booted, check for the partition table

> sudo fdisk -l

 post the output.

---

### Post by kristapsl on 2009-10-30
[maxideci]("http://ubuntuforums.org/member.php?u=768580") Can not do that, because the same problem.

---

### Post by maxideci on 2009-10-30
Hi, 

sorry about that, my suggestion is to boot using win7-dvd and instead of "install" select "repair" after the initial selection of language->keyboard layout->time zone.

you can google about how to fix booting problems using win7 dvd or something.

I do not know if I can post links on this forum.

once you get back your windows system, we can start working with ubuntu-LiveCD.

Cheers!!

---

### Post by kristapsl on 2009-10-30
> **maxideci said:**
> Hi, 

sorry about that, my suggestion is to boot using win7-dvd and instead of "install" select "repair" after the initial selection of language->keyboard layout->time zone.

you can google about how to fix booting problems using win7 dvd or something.

I do not know if I can post links on this forum.

once you get back your windows system, we can start working with ubuntu-LiveCD.

Cheers!!

Reinstall all windows7 tried to install ubuntu still the problem. Before I tried upgrade 9.04 to 9.10 everything were ok. Now I can not install even ubuntu 8.04. It lets just choose language and installation menu. After that screen gets black cd room working for 5 minutes and then get silent. Formated also patrition where were ubuntu 9.04

---

### Post by maxideci on 2009-10-30
Hi, 

I am sorry, this is beyond my understanding, wait for some experience guy to reply. I am also just beginner like you.

cheers!!!

PS. what do you see when u start disk manager in windows.
Accessories->Administrative Services->Computer Management->Disk Manager
It shows the partitions table.

---

### Post by kristapsl on 2009-10-30
It looks like this
[http://img259.imageshack.us/img259/7353/diskjpg.jpg](http://img259.imageshack.us/img259/7353/diskjpg.jpg)

---

### Post by maxideci on 2009-10-30
Hi, 

It doesn't show any Linux Partitions. Create a raw partition before installing ubuntu.

but anyway, did you try installing ubuntu within windows ?? you just can see if things go your way.

do you have bootable cd/dvd of any other distros ??? just to check what msg you get when u boot from other CD. try it.

cheers!!

---

### Post by kristapsl on 2009-10-30
> **maxideci said:**
> Hi, 

It doesn't show any Linux Partitions. Create a raw partition before installing ubuntu.

but anyway, did you try installing ubuntu within windows ?? you just can see if things go your way.

do you have bootable cd/dvd of any other distros ??? just to check what msg you get when u boot from other CD. try it.

cheers!!

1) it did not show any, because i formated HD
2) Partition D i prepared for ubuntu
3) Yes I had installed on windows 7
4) I already tried ubuntu 8.04, the same problem

---

### Post by maxideci on 2009-10-30
Please also refer [http://ubuntuforums.org/showthread.php?t=1304562](http://ubuntuforums.org/showthread.php?t=1304562)

cheers!!!

---

