---
title: "ubuntu doesn't boot on toshiba laptop"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by peaceofourlord on 2009-10-24
I reformatted my drive and installed unbuntu on the machine. 
It doesnt boot.  I can run Ubuntu off the CD Rom, but I am trying to get the laptop to recognize the bootloader. 

Any ideas?

---

### Post by dandnsmith on 2009-10-25
Help yourself by posting:
1. the Ubuntu version
2. the laptop model (may have known problems)
3. whether it's a dual boot (if so, which Windows)
4. what happens when you boot

---

### Post by peaceofourlord on 2009-10-25
Installed Ubuntu 9.04 desktop, acquired from ubuntu website this week. 
Copied image to hard drive. 

I gave up on the ubuntu flying solo - it is now partitioned with windows on one partition. 

Either way, ubuntu does not present itself to boot.  Laptop is a Toshiba Satellite 1005 S157.

I have no idea how to edit the kernel so I could use help

a) understanding how the kernel needs to be modiefied.
b) how, exactly, I modify the kernel. I can boot ubuntu form the Cd rom. 

thanks

---

### Post by Mark Phelps on 2009-10-25
> **peaceofourlord said:**
> I have no idea how to edit the kernel so I could use help

a) understanding how the kernel needs to be modiefied.
b) how, exactly, I modify the kernel. I can boot ubuntu form the Cd rom. 

thanks

You do NOT need to be modifying the kernel. It's very unlikely that has ANYTHING to do with your boot problem.

Please answer the questions previously asked:
3. whether it's a dual boot (if so, which Windows), in other words, is Ubuntu installed in it's own partition or did you install it using Wubi inside Windows? And, which version of Windows is it (XP, Vista)?
4. what happens when you boot, as in, what exactly do you see -- on screen, error messages, etc.

We're not mind readers here.

---

### Post by wsscott on 2009-10-25
Had (have) the same problem with my toshiba laptop.  I updated the BIOS but it didn't help.  The laptop had XP installed.  I installed Jaunty within XP (wubi).   Starts like a dual boot PC when laptop is powered on....choose XP or Jaunty.  XP is the default.  Seems to work fine.

---

### Post by Mark Phelps on 2009-10-25
> **wsscott said:**
> Had (have) the same problem with my toshiba laptop...

Since the OP has not yet responded with whether or not this is a Wubi install, we really don't know if yours is the same problem or not ... now do we?

---

### Post by dandnsmith on 2009-10-26
I agree that we still need information.
There's a hint that Ubuntu and Windows may be on separate partitions - but then you might read it the other way (implying a wubi install).
Copying the image to HDD might mean it isn't properly installed.
Lacking the Windows version, we don't know which nasties might be present.

Perhaps OP may respond!!

---

### Post by lupus on 2009-10-29
Toshiba Satellite L30-101

It doesn't boot when using battery, but with connected power suply boot without problems.

---

### Post by Hb_Kai on 2009-11-03
Lupus: 
You should maybe consider buying a new battery. 
Current lifespan for most batteries, I'd say on average, 3 - 4 years before they start dying.

---

