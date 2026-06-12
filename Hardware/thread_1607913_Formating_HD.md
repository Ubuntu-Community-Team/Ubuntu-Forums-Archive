---
title: "Formating HD"
date: 2010-10-28
forum: Hardware
---

### Post by jharl on 2010-10-28
Hi all,

I have installed Ubuntu 10.04 LTS on my desktop. I have a formatting question.

My config:
Dell GX 280 2GB ram, 80 GB HD Attached to mainboard. 
Highpoint Rocket 620A 2 750GB HDs on seagate and the other WD.

Question is I format the 750 gb hd and I am not getting the full 750gb, what can I do to get more space out of the drive. I am getting 698GB. If that is all I can get please let me know.

jharl

---

### Post by KaiO on 2010-10-28
Install partitionmanager (or gparted) with your package manager to get a graphical view of your disks.

---

### Post by krishnandu.sarkar on 2010-10-28
Ya we don't get full space for use HDD's or USB's too.

So don't worry :)

---

### Post by dtfinch on 2010-10-28
750gb = about 698.5gib
[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

Later, if you format it ext2/3/4, you can use "tune2fs -m0" on the partition to reduce the reserved space to 0% to get the most space out of it. The default reservation is 5%. I usually go with -m1 for 1%.

---

### Post by DirtyPC on 2010-10-28
Spot on there, you never get quite what it says on the tin, and if you ever challenge it, then can catch you out with Gigabits/bytes and stuff like that, you'd think If they advertise 750gb, they'd actually put 802gb so you got what was advertised... :mad:

---

### Post by jharl on 2010-10-28
WOW totally fast response guys. Yea I did not expect to get the full drive, but 50gb seemed like and awful lot to give up. ok nothing wrong partition is as described.

thanks muchly

jharl
:guitar:

---

