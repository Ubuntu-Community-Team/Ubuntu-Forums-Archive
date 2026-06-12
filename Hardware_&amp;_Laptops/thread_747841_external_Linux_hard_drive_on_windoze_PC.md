---
title: "external Linux hard drive on windoze PC"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by Bill J64 on 2008-04-06
Greetings!

I hope I've offered this post to the correct forum, if not please redirect me to the appropriate forum.  Thanks.

I have a Windoze PC, built by a local shop using a Intel Pentium 4- 2.8 GHz processor.  I am currently running XP.  My hard drive is pretty much full.  I was thinking of adding an external hard drive and using it exclusively for Linux Ubuntu.  I'm not terribly geeky and wonder about the wisdom and usefulness of this approach.

Questions I have:

I would like to be able to boot from either OS at will.  Is that practical/possible?  

What is involved?  

Anything in particular I should know about which external drive to select?

How does one go about mounting Linux Ubuntu on an external drive from an XP environment?

Any comments would be most appreciated.

Cheers,

Bill J64

---

### Post by sdennie on 2008-04-07
I don't really think you will have any issues installing to a USB connected drive.  The last time I installed Ubuntu, I had an SD card in my machine (the little cards that cameras use) and Ubuntu offered to install the entire OS onto that card but, based on previous experience it was going to write the bootloader (grub) onto the primary hard drive.  If you have XP installed, the Ubuntu installer is smart enough to add XP as a boot option for grub so you can easily choose to run XP or Ubuntu at boot time.

Honestly, if you just boot from an Ubuntu 7.10 install disk, it will probably do exactly what you want without any hassle at all.  Make sure to tell it to install to the USB disk and everything is likely to just work.

---

### Post by Ozzz on 2008-04-08
As the above post says, installing from the LiveCD should accomplish your goal.

My current install is running duel boot XP-Pro/Ubuntu 7.10

I installed Ubuntu on an external USB WD Passport 160 drive. I first repartitioned the 160 in half. Formated half as fat32 used for a storage for both XP and Ubuntu; the second half has the Ubuntu install ext3. After formatting I gave the USB drive the name USB01 on the fat32 side so I could easily see it.

When the external drive is plugged in I get the duel boot option, if not I boot right into XP.

---

