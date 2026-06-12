---
title: "Ubuntu inst HP pavilion DV7 6105 SD"
date: 2011-11-19
forum: Hardware
---

### Post by EMCees on 2011-11-19
I recently bought a HP Pavilion DV7 6105 SD laptop.

It uses a dual core GPU, when i try to install UBUNTU 11.10 it shows up with a black screen during the instalation, same behaviour with the trial option. So i can't install ubuntu.

I think the installation kernel can't handle dual core GPU systems.

Any pointers for a solution...
Product number LZ063EA#abh
bios version F.21 insyde

tnx in advance,
Cees

BTW same behaviour with opensuse install.

---

### Post by Mark Phelps on 2011-11-22
It's not the dual-core per se, I know because I had it installed on 2-core, 4-core, and 6-core systems without problems.

What it may be is switchable graphics.  Some of the DV6 and DV7 HPs use that, and Ubuntu can't handle that well -- which is demonstrated by lack of graphics.

---

### Post by SeijiSensei on 2011-11-22
If the initial Ubuntu menu screen appears upon booting, try hitting F6 and picking "nomodeset" from the options listed.  Then hit enter and see if you have better results.

---

### Post by ifeelgreat on 2011-11-23
Just to clarify, SeijiSensei is referring to  the "Graphics adapter Processor Unit" [GPU] with a "dual core" in his HP Pavillion dv7 6105 SD, not the number of cores of the CPU.

> **Mark Phelps said:**
> It's not the dual-core per se, I know because I had it installed on 2-core, 4-core, and 6-core systems without problems.

---

### Post by Mark Phelps on 2011-11-23
> **ifeelgreat said:**
> Just to clarify, SeijiSensei is referring to  the "Graphics adapter Processor Unit" [GPU] with a "dual core" in his HP Pavillion dv7 6105 SD, not the number of cores of the CPU.

Thanks for the clarification ... missed that.

So, if by dual-core, the OP means two different GPUs, that goes back to the switchable graphics problem, which for the Dv7's, does not appear to be solvable.

---

### Post by SeijiSensei on 2011-11-23
> **ifeelgreat said:**
> Just to clarify, SeijiSensei is referring to  the "Graphics adapter Processor Unit" [GPU] with a "dual core" in his HP Pavillion dv7 6105 SD, not the number of cores of the CPU.

"Just to clarify," I didn't say that, the OP did. :D

You might be able to get around this problem by [changing a setting in the BIOS]("http://ubuntuforums.org/showthread.php?p=11244073#post11244073").

---

### Post by EMCees on 2011-11-25
I did have a look at the bios, but it doesn't allow me to change video behavior.
I checked all interfaces, so HDMI and VGA external.

But no success yet.
It still shows up with a black screen whilst trying to install any linux, (fedora, red hat opensuse ubuntu)

And indeed it is a dual core Graphical processing unit, not a n core amd or intel Central Processing Unit.

STill trying,

Cees

---

### Post by SeijiSensei on 2011-11-26
> **EMCees said:**
> I did have a look at the bios, but it doesn't allow me to change video behavior.

What version of the BIOS is it?  As I wrote in the posting I referenced above, only the most recent HP firmware has this option.  You may to upgrade the firmware; again see that posting for details.

---

### Post by EMCees on 2011-11-27
I have installed the latest bios, no switch or what so ever to change video behaviour.
So no suc6 yet.

And obviously i would like to see something during installation. :P

Radeon dual graphics it says on a small sticker

---

### Post by pcrepairguy on 2011-12-23
> **EMCees said:**
> I recently bought a HP Pavilion DV7 6105 SD laptop.

It uses a dual core GPU, when i try to install UBUNTU 11.10 it shows up with a black screen during the instalation, same behaviour with the trial option. So i can't install ubuntu.

I think the installation kernel can't handle dual core GPU systems.

Any pointers for a solution...
Product number LZ063EA#abh
bios version F.21 insyde

tnx in advance,
Cees

BTW same behaviour with opensuse install.

I have the same problem with ubuntu 11:10 & Mint 12. I tried to find a solution but now luck finding a driver for Linux around. 

Any ideas?

---

### Post by Mark Phelps on 2011-12-23
> **pcrepairguy said:**
> I have the same problem with ubuntu 11:10 & Mint 12. I tried to find a solution but now luck finding a driver for Linux around. 

Any ideas?

Is this the same hardware?  IF so, you too are a victim of the switchable graphics problem.

Details are provided below:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by railen5 on 2011-12-30
> **EMCees said:**
> I did have a look at the bios, but it doesn't allow me to change video behavior.
I checked all interfaces, so HDMI and VGA external.

But no success yet.
It still shows up with a black screen whilst trying to install any linux, (fedora, red hat opensuse ubuntu)

And indeed it is a dual core Graphical processing unit, not a n core amd or intel Central Processing Unit.

STill trying,

Cees
I have this same problem, I dual boot on all of my computers but I just  was given a new laptop for Christmas and I tried Ubuntu from a  thumbdrive as well as using wubi installer and the screen goes black  after boot up. One more note, I have noticed that the Linux Distro, Debian Live  works normally on this AMD graphics card.

---

### Post by Olmanstatic on 2011-12-30
I have the same labtop :D and problem :(. Have anyone solved the problem yet? Hopefully they will fix it in 12.04 final release.

---

### Post by Olmanstatic on 2011-12-30
> **railen5 said:**
> I have this same problem, I dual boot on all of my computers but I just  was given a new laptop for Christmas and I tried Ubuntu from a  thumbdrive as well as using wubi installer and the screen goes black  after boot up. One more note, I have noticed that the Linux Distro, Debian Live  works normally on this AMD graphics card.

So you got one on your labtop? How did you get it to work?

---

