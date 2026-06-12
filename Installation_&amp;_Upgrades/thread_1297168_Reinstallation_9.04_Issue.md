---
title: "Reinstallation 9.04 Issue"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by brucethedog on 2009-10-21
Hi
 
Newbie to the scene.
 
I have an Acer Aspire 3000 whic last week suddenly stopped working in XP.
It would load, work for a while, then hang.
Tried to reinstall XP after the usual msconfig stuff, and it still would hang.
 
So I downloaded Ubuntu 9.04 desktop x86 ISO, created a boot disk, and it installed with no issie. It used the whole 100Gb for the new install.
 
This was fine, managed to get DVD's playing, sound and the wireless working fine, using tips/hints from this board.
 
Yesterday, I tried an update, and got errors about Public key which I cured using a wired conenction, but my wireless died. Tried to recreate but no joy.
Wireless is working fine on my Vista laptop, and the PS3 can see as well.
 
Anyway, I thought I would reinstall Ubuntu over the disk, and it boots fine, got to the menu and selected Install Ubuntu.
 
Its been flashing my hdd light and CD light for hours now and I'm not sure whats going on.
Its not moved from that initial screen and I cant select any options to do this reinstall. Tried resetting same issue. Tried killdisk to flatten hdd, which ran fine, but still same issue.
 
Do I need to reformat that linux partition? If so how?
If not, anyone know what my issue could be?
 
Thanks
 
BruceTheDog

---

### Post by g160689 on 2009-10-21
Use the windows xp cd to delete partition and try to reinstall ubuntu completely..this time dont use the whole 100gb

---

### Post by howefield on 2009-10-21
Try loading the live cd to the desktop, and use the partition editor (System > Administration > GParted) to make your partitions, then install Ubuntu using the icon on the desktop.

---

### Post by Zimmer on 2009-10-21
> **brucethedog said:**
> Hi
 
Newbie to the scene.
 
I have an Acer Aspire 3000 whic last week suddenly stopped working in XP.
It would load, work for a while, then hang.
Tried to reinstall XP after the usual msconfig stuff, and it still would hang.
 
So I downloaded Ubuntu 9.04 desktop x86 ISO, created a boot disk, and it installed with no issie. It used the whole 100Gb for the new install.
 

 
Do I need to reformat that linux partition? If so how?
If not, anyone know what my issue could be?
 
Thanks
 
BruceTheDog

Perhaps a bit of reading about partitioning before you set out to re install..
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Basically, if you have a whole hard drive to commit to Ubuntu it is a good idea to put /home in its own partition, makes re installing a newer version less painful. Also, if you have space, maybe a separate partition just as a data store area.. have a read ... which will lead you to ask some more questions.. ;)

As for your XP 'hanging': could have been a driver issue, but do not rule out a hardware problem (overheating, vents blocked, fan not functioning etc)..

---

