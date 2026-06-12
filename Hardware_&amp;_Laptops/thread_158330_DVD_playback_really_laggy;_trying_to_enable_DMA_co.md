---
title: "DVD playback really laggy; trying to enable DMA completely freezes computer"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by Twilight Lamentation on 2006-04-11
Hi,
I'm running 5.10 (Breezy Badger?) on my Dell Inspiron8200, and I've run into a series of issues trying to play DVDs. After much finangling, I got that codec that's required, and now I can play DVDs, but they play really, really badly; much worse in VLC than in xine, but they still keep hanging up for a split-second every single second even in xine. I tried to enable DMA using:
sudo hdparm -d1 /dev/hdb

which utterly froze my computer.  The harddrive activity light just went solid (nevermind the fact that hdb is my cd/dvd drive), and the computer didn't respond to anything other than holding down the power until it shut off.

Does anyone know what's going on?

And is it just me, or does it seem kinda riduculous that I can easily play all of my pirated movies without any problems, but have to leap through flaming hoops and crash my computer trying to play my legit DVDs?

---

### Post by slipk487 on 2006-04-11
install automatix it has a option for enabling dma

---

### Post by Twilight Lamentation on 2006-04-11
Synaptic couldn't find Automatix.

---

### Post by slipk487 on 2006-04-14
it not in there this is wat u have to do to get it

```
wget http://beerorkid.com/automatix/automatix_5.7-3_i386.deb
```
then type this
```
sudo dpkg -i automatix_5.7-3_i386.deb
```

and when its done it will be in apps>sys tool>automatix then run it will start and say autoscript and ask for ur password to run it then a screen will popup with the programs and fixes it can install and u chose want u want it to install

---

### Post by Twilight Lamentation on 2006-04-17
Ok well Automatix enabled DMA, but now Ubuntu can't detect my cd/dvd drive at all! When I try mounting it, it says: special device /dev/hdb does not exist.
Is there any fix for this, other than disabling DMA and just accepting the fact that Ubuntu will not play DVDs properly?
thanks

*ponders going back to Windows, except for the nice little fact that her cd drive won't work now!*
*sigh*

---

