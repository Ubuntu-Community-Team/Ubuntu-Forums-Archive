---
title: "Unable to Install Ubuntu 8.04 or 8.10"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by livingfully on 2008-12-11
Alternate CD install fails at 85 pct on libgl1-mesa-dri. My hardware is Asus CUSL2 (socket 370) motherboard with 900 mHz Intel processor, 256k PC133 ram and Abit GF4 MX video graphics card. Md5sums are good. The 8.04 CD was successfully used to install Ubuntu on another PC. 

Thanks for your suggestions,

Doug

---

### Post by icanfly0307 on 2008-12-11
Hey there. What speed did you burn your CD at? If you burnt it at the highest speed possible, it won't work. Try burning it at the *slowest* speed possible and try again.

Good Luck!

---

### Post by Kevbert on 2008-12-11
Have you tried running memtest on this PC ? When the install fails do you get any messages ?

---

### Post by Mark Phelps on 2008-12-11
Should tell you that unless you can (and do) upgrade the RAM on your machine beyond 256MB, you won't be happy with Ubuntu.  I installed it on a similar box and it was so slow as to be all but useless.

If you're going to use such an "underpowered" (in today's terms) machine, you need to looking into alternatives like DSL (Damn Small Linux), Puppy Linux, or Zen-Mini (minimal version of PC LOS 2008).

---

### Post by Drostie on 2008-12-11
Mark Phelps has the right idea here. I ran Ubuntu on a laptop which had 512 MB of RAM, but the motherboard reserved something like 128 MB of it for the video card. With the 384 MB remaining, I couldn't really do all of the multitasking that I'd wanted. 

However, that isn't an answer to your question.

This is: You're presumably using the alternate CD for the native encryption support? That's the popular use. (I'm guessing here, and if my guess is wrong, then none of the following advice applies.)

There is a several-hours-long step in hard drive encryption where the system writes random data to disk, erasing anything that was on it beforehand. As far as I can tell, after this step, the alternate installer uses more memory than before the step. With another system with 512 MB of memory, I was running out of memory during the install phase after this step.

So: do the erasure step with the alternate install CD, then, before it gets too much further, get to the supermenu (a table of contents containing all of the steps individually) by some combination of the escape key and the Go Back options.

Once you're at the supermenu, tell it to abort the installation. This will reboot the alternate installer.

Now that the installer is rebooted, select your newly-erased partition as "free space for encryption" (or whatever the option is), but elect **not** to erase it, as it's already erased. 

With hope, the rest of the alternate installer still has enough memory to complete. 

Good luck.

---

### Post by livingfully on 2008-12-11
I recorded the CD at 24x, when the maximum speed possible is 52x, and the 8.04 CD was used to install Ubuntu on another computer. My Cd recorder has been trouble-free.

Memtest was ok. That's the first thing I checked.

I don't want disk encryption.

I realize that 256k ram is low. I'll add more ram if I can install Ubuntu successfully.

A search turned up a few hits on libgl1 bugs during an upgrade, but I didn't find anything related to a fresh install.

Doug

---

### Post by icanfly0307 on 2008-12-11
Is 24x the slowest possible?

---

### Post by used2bnewb on 2008-12-11
Is this the desktop CD or alternate install

And with that RAM I'm not sure if either would work

---

### Post by icanfly0307 on 2008-12-11
Actually, I've installed Ubuntu on my computer which has 256MB of RAM too and it works great. However, it's not so good for multi-tasking. I can run my music player and web browser simultaneously but nothing more than that.

And yes, he's got to be using the Alternate Install CD (First sentence of first post :) ). The LiveCD won't work unless he's got 384MB of RAM.

---

### Post by livingfully on 2008-12-12
24x is not the slowest speed I can write a Cd. If Cd write quality is an issue, I think I can extract the iso and run get the rm5sum to verify a clean write. 

Yes, I'm using the alternate Cd.

---

### Post by icanfly0307 on 2008-12-12
Try burning at the lowest speed. I'm guessing it's 16x

---

