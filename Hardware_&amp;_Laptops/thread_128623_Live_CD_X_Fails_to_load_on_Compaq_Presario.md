---
title: "Live CD: X Fails to load on Compaq Presario"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by AusIV4 on 2006-02-11
First off, I have to say how much I've enjoyed working with Ubuntu. I'm running Ubuntu on a relatively old desktop, primarily for storage via samba, but I also toy around with it in gnome and KDE.

For reasons that are probably obvious to most of the people on this board, I've decided I'd like to move my primary computer over to Ubuntu as well. I've got a Compaq Presario X6000, and it doesn't seem to like the Breezy live CD (Hoary works fine). When I try to boot the live CD, I get an error saying X has failed to start, then it goes to a command line.

I've tried the same LiveCD on another computer, so I know the CD is not corrupt, and I've used the Hoary LiveCD on the computer in question, and it worked just fine.

My graphics card is an ATI Mobility Radeon X600. I have a P4 3.0 GhZ and 512 MB of RAM.

It's crossed my mind that it may be a Live CD issue that wouldn't come up if I installed it, but for obvious reasons I'm hesitant.

Can anybody tell me where to look for solutions?

---

### Post by K.Mandla on 2006-02-11
Before I answer, I have to make a disclaimer: I haven't done this, so I don't know if it would work. But it strikes me that if the Hoary CD is OK, try installing Hoary, then making the [upgrade to Breezy]("https://wiki.ubuntu.com/BreezyUpgradeNotes"). 

It would kind of add a step, but if there's something about straight Breezy that your laptop doesn't like, why not just step around it? ;) 

Again, I haven't ever done that (I haven't needed to), but it's an idea. If it doesn't work, please correct me. :rolleyes:

---

### Post by BananamansNut on 2006-02-11
Hey AusIV

Can you post /var/log/xorg.0.log to show the error?

I've got the same problem with an aussie Compaq Presario V2000 (2400 i think? can't remember)  It is something to do with the cards modules not initialising properly i think - but it could also be the X driver the live cd is using.  If you try installing then make sure your network is working & see if you can try the fglrx drivers - it *might* fix your problem.

My problem is with the radeon xpress 200M - the error i get is something to do with the dri.

---

### Post by AusIV4 on 2006-02-12
Here is a link to my [Xorg.0.log]("http://ausiv.selfip.com:85/ausiv/Xorg.0.log"). It's pretty big (large enough the forum wouldn't let me upload it). It's hosted on my server, which has notoriously bad reliability (thanks to my university internet connection), but hopefully it'll be up when people try to download it.

Hopefully it will provide some useful information.

---

### Post by AusIV4 on 2006-02-12
The thought crossed my mind that perhaps I was being silly trying the Ubuntu live CD when I intended to use Kubuntu on the machine. So I burned a Kubuntu live CD and got pretty much the same result. A diff of the /var/log/Xorg.0.log files only showed differences on lines that had timestamps.

The only difference between the CDs was that the Ubuntu Live CD told me X wouldn't start, Kubuntu just went straight to a command line.

Whatever that's worth.

-AusIV

---

### Post by slavik on 2006-02-12
try edditing the file and using "vesa" instead ...

same thing happened on my laptop (xpress 200m also) after setting the driver to vesa (until installing ati drivers) it worked out fine :)

---

### Post by Mustard on 2006-02-12
As above I would suggest that you run this command below and reconfigure xorg.conf to use vesa drivers as a temporary measure until you get a GUI and can then look into installing ati drivers...

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by slavik on 2006-02-12
after installing the drivers, I even installed ut2k4 :D

it runs slow (need to tweak settings, but won't go further than 640x480 with lowest settings prolly, but hey, this is not a gaming system). maybe even doom3?

---

