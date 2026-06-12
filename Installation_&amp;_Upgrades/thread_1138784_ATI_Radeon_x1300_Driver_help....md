---
title: "ATI Radeon x1300 Driver help..."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by claymater on 2009-04-26
So after my past fails on trying to install 9.04, I looked around the net, and seem to have found that it was a driver problem (oh how I love ATI + linux.....) People are saying that there isnt a driver out yet, so it wont work (or something). Is this true? If so, ill just keep 8.10 for a bit till it comes out.

---

### Post by Mark Phelps on 2009-04-27
The most current ATI driver, Catalyst 9.4, has dropped support for "older" cards -- so even if you download and install it, it won't do you any good.  There's no point in waiting for an update from ATI -- it's not going to happen.

---

### Post by Dearhell on 2009-04-27
I have an ATI Radeon Mobility x300 and have the same problem.

Does this means that we can't never upgrade from ubuntu 8.10?

---

### Post by Mark Phelps on 2009-04-27
> **Dearhell said:**
> I have an ATI Radeon Mobility x300 and have the same problem.

Does this means that we can't never upgrade from ubuntu 8.10?

No, it means that if you have one of the video chips that ATI dropped support for in Catalyst v9.4, you won't be able to get any proprietary drivers from ATI anymore.

And, since only Catalyst 9.4 and newer ATI drivers will work with the Xorg v1.6 in 9.04, you can't install and use Catalyst 9.3 drivers, either.

So, anyone using a video chip that ATI abandoned will have to use the open source drivers instead in Ubuntu 9.04 or newer.

---

### Post by claymater on 2009-04-27
So what do I do, I WANT TO GET JAUNTY!!!!! *cry face*..... 
Is there any way to install? (I dont get any screen, It just goes to black.... I sad)

---

### Post by claymater on 2009-04-27
Any ideas?

---

### Post by kha on 2009-04-28
I'm in the same situation. I've upgraded to Ubuntu 9.04, since i use my laptopt to develop, not to play. I have an ATI X1300 and support has been droped in new catalyst drivers.

So i use the opensource ati drivers using this configuration file:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7156021](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7156021)

It works, but my screen sometimes flicker... I don't know why... If anyone can help...

Thank you !

---

### Post by sir83 on 2009-04-28
Hi,
 
I have a familiar card in my laptop. Ati x1250.
 
I'm using the radeonhd driver and have a issue with some flickering.
 
It would be nice if someone found a solution to this problem. It really grinds my gear.

---

### Post by claymater on 2009-04-28
I have thought about different distros.. but I dont think that will work, since the main problem is with ATI.... (sad)

---

