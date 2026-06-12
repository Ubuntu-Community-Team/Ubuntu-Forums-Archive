---
title: "Possible to upgrade partition from current to higher?"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by D3mon_Spawn on 2009-09-29
I just started using Ubuntu and when I installed it on my machine I chose the second option from the live CD; which was to install it inside windows and use the windows boot-loader to start up ubuntu. I remember while I was doing this I had the option to choose a size for my Ubuntu section of the hardrve (I chose 20gb). I was just wondering if it was possibe to increase this space after it has been already installed. I wasnt sure if this is possible or not since a new partition isnt actually created. All help is greatly appreciated. :)

---

### Post by drs305 on 2009-09-29
You have a couple of options but the short, easy answer is that a wubi install inside Windows isn't really designed to be expanded.

Here is a link the wubi wiki and targeted to the 'expansion' section. Actually, scroll up a bit:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")

---

### Post by D3mon_Spawn on 2009-09-29
thx

---

### Post by drs305 on 2009-09-29
D3mon_Spawn  	

20GB should be more than big enough for most Ubuntu installs if you keep your data separate. Ubuntu can read NTFS partitions and you can mount your Windows or data partitions so you don't have to put everything inside the wubi file. 

Many users treat wubi as a test to see if they like Ubuntu. When they do they install it on a normal partition. If you have some specific goals we can probably steer you towards a solution. 

By the way, welcome to Ubuntu and the Ubuntu forums.

---

### Post by D3mon_Spawn on 2009-09-29
I see what you mean. The only reason I'm using Ubuntu through Wubi is because I don't have any way to back-up my windows partition; so if I installed Ubuntu the normal way through a separate partition (since I would like to dual-boot) there is a slight risk I can lose the Windows partition. I know this seems a little silly but I'm new to using partitions and boot-loaders so this is the best thing I can do for now.

---

