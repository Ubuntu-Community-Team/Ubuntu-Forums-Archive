---
title: "Colored Vertical Bars"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by Marlon12 on 2009-08-13
When installing Ubuntu 9.04 Desktop x86 on my Pentium 4 box, I get a screen with a whole bunch of colored vertical bars after choosing to install Ubuntu.

I'm thinking this might be hardware related, though.  Is this something anyone has ever seen before?

---

### Post by Marlon12 on 2009-08-13
*Bump*

Any insight into this issue, guys?

---

### Post by Mark Phelps on 2009-08-14
Well, you should have run the LiveCD first to ensure that you can at least get working video.

You mention Pentium 4, which if it's a 478 form factor chip, is quite "old", which shouldn't present a CPU-related problem but if the video is the same vintage, there's every possibility that there is no working Linux video driver.

So, what's the make and model of your video card/chip?

---

### Post by Marlon12 on 2009-08-14
> **Mark Phelps said:**
> Well, you should have run the LiveCD first to ensure that you can at least get working video.

You mention Pentium 4, which if it's a 478 form factor chip, is quite "old", which shouldn't present a CPU-related problem but if the video is the same vintage, there's every possibility that there is no working Linux video driver.

So, what's the make and model of your video card/chip?

It's a Pentium 4 socket 775 processor.  My video card is an nVideo (not sure of the model, bought it three years ago)  PCI express 16x AVI card.  I can't imagine that Ubuntu wouldn't included an nVidia driver.

---

### Post by Mark Phelps on 2009-08-14
> **Marlon12 said:**
> It's a Pentium 4 socket 775 processor.  
OK, that's current.

> My video card is an nVideo (not sure of the model, bought it three years ago)  PCI express 16x AVI card.  I can't imagine that Ubuntu wouldn't included an nVidia driver.
Ubuntu includes open source drivers by default.  Nvidia and AMD/ATI drivers are known as "restricted" because they are NOT open source and are, consequently, NOT automatically installed.

However, if there is an Nvidia restriced driver available for your card, one that works with the current kernel you have installed, you should be offered it as a matter of routine. 

Go to System --> Administration --> Hadware Drivers and see if it offers you anything.

Sorry, just realized that you probably can't get to a desktop; OK, so boot from the LiveCD and do the same thing.  IF it offers you a driver, then you know there is one available from Nvidia.

---

### Post by presence1960 on 2009-08-14
when you get to the screen attached below hit F4 and choose safe graphic mode. For more info: [boot options]("https://help.ubuntu.com/community/BootOptions")

if all else fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Marlon12 on 2009-08-15
> **presence1960 said:**
> when you get to the screen attached below hit F4 and choose safe graphic mode. For more info: [boot options]("https://help.ubuntu.com/community/BootOptions")

if all else fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

Installing in safe graphics mode did the trick.  Thanks to both of you for your help and for contributing to this wonderful project!

---

### Post by presence1960 on 2009-08-15
> **Marlon12 said:**
> Installing is safe graphics mode did the trick.  Thanks to both of you for your help and for contributing to this wonderful project!

Glad you got it working...Enjoy Ubuntu!

---

