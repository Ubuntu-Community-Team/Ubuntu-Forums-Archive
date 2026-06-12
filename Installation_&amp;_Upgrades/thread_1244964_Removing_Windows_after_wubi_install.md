---
title: "Removing Windows after wubi install"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by varunmagical on 2009-08-20
Hello,
I have installed ubuntu 9.04 through windows xp using wubi.
Now I want to get rid of windows.. but I have thousands of applications installed on ubuntu & I dont want to lose my work & setting ( I dont have fast internet connection to install all that stuff again)
Please guide me How can I make That wubi partition "Real"

---

### Post by rcayea on 2009-08-20
I don't think you are able to do what you are suggesting because I believe Wubi is actually an .exe file and is just a program on Windows. 

I'll google this and see what I come up with. 

Randy

---

### Post by wojox on 2009-08-20
Yes you're right if you wipe out windows you'll take wubi with it.

---

### Post by rcayea on 2009-08-20
Maybe you could partition your hard drive into two separate partitions and then install Ubuntu in the new partition. Once you have Ubuntu installed maybe you could copy over the programs from windows. This way you wouldn't have to rely on your internet connection.

---

### Post by varunmagical on 2009-08-20
> **rcayea said:**
> Maybe you could partition your hard drive into two separate partitions and then install Ubuntu in the new partition. Once you have Ubuntu installed maybe you could copy over the programs from windows. This way you wouldn't have to rely on your internet connection.

By programs, I mean I have many installed softwares so I cannot just "copy" them.
Is there any way that I can backup my entire system( Including installed programs & settings) & restore them on fresh ubuntu install?

---

### Post by lisati on 2009-08-20
> **varunmagical said:**
> By programs, I mean I have many installed softwares so I cannot just "copy" them.
Is there any way that I can backup my entire system( Including installed programs & settings) & restore them on fresh ubuntu install?

I don't know how well it will work with a wubi-based installation, but there's [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") which can create a "Live CD" version of your current installation. You'll probably have to find some way of copying your data across (the previously mentioned partitioning option might be one way to go)

---

### Post by varunmagical on 2009-08-20
> **lisati said:**
> I don't know how well it will work with a wubi-based installation, but there's [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") which can create a "Live CD" version of your current installation. You'll probably have to find some way of copying your data across (the previously mentioned partitioning option might be one way to go)

I have heard about remastersys. But my existing wubi installation is 30 GB!
What I want is good backup/restore system that can backup my system entirely.
I have seen many backup/restore programs but they just allow me to backup settings.

---

### Post by varunmagical on 2009-08-20
will lpvm work?

---

### Post by Partyboi2 on 2009-08-20
Using [[COLOR=Blue]LVPM[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") will allow you to move your Ubuntu installation to its own Partition.

---

### Post by varunmagical on 2009-08-21
> **Partyboi2 said:**
> Using [[COLOR=Blue]LVPM[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") will allow you to move your Ubuntu installation to its own Partition.
Does that mean my new installation will be bootable?
because current boot manager is in c:\ where windows xp resides..
will that new Ext4 partition be bootable?
Also, I have read on lvpm site that its tested with 8.04 , does it work with Jaunty?
Thank you!

---

### Post by varunmagical on 2009-08-21
> **Partyboi2 said:**
> Using [[COLOR=Blue]LVPM[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") will allow you to move your Ubuntu installation to its own Partition.

Thanks a lot for that wiki link you have provided.. I will try that.
They have mentioned some alternative there... does that work with Jaunty?

I have 320 GB drive & dont want to screw up my E: & F: !!

I have copied all my important data from my c: & d: to e: & f:

I am gonna use crappy windows xp & 7 using virtualbox ( for my dos based clg work like Turbo C!)

---

