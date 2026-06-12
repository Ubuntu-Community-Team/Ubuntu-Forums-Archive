---
title: "Hard Drive Upgrade with Image"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by eviltang on 2006-12-23
First and foremost, thank you and everyone who makes Ubuntu what it is.  However, I am having a (self-inflicted) problem that I can't seem to figure out what it is.

Here is my situation.  I have a Compaq C 300 (C307NR to be specific).  The OEM HDD that came  with it is an SATA 80GB 5400RPM drive.  I have upgraded to a new HDD (SATA 100GB 7200RPM), but now overall system performance is very slow.  

The process I used to accomplish this is as follows (for simplicity sake, I will not go into too much detail);

1.  back up HDD with Acronis to external USB HDD
2.  install new HDD (ensuring that BIOS sees the correct size/no conflicts)
3.  restore image to new HDD
4.  Boot.

I have not resized/altered my partition, everything boots, all of my apps work, however it is extremly slow.  

Is there a way that I can reenumerate the Hardware, or is there a setting that I need to alter in order to take advantage of the new drives capabilities?

Thanks again.

Respectfully,

Eviltang

---

### Post by budgie9 on 2006-12-23
> **eviltang said:**
> First and foremost, thank you and everyone who makes Ubuntu what it is.  However, I am having a (self-inflicted) problem that I can't seem to figure out what it is.

Here is my situation.  I have a Compaq C 300 (C307NR to be specific).  The OEM HDD that came  with it is an SATA 80GB 5400RPM drive.  I have upgraded to a new HDD (SATA 100GB 7200RPM), but now overall system performance is very slow.  

The process I used to accomplish this is as follows (for simplicity sake, I will not go into too much detail);

1.  back up HDD with Acronis to external USB HDD
2.  install new HDD (ensuring that BIOS sees the correct size/no conflicts)
3.  restore image to new HDD
4.  Boot.

I have not resized/altered my partition, everything boots, all of my apps work, however it is extremly slow.  

Is there a way that I can reenumerate the Hardware, or is there a setting that I need to alter in order to take advantage of the new drives capabilities?

Thanks again.

Respectfully,

Eviltang

Being as you are not getting an answer, can I say this in the hope it helps you.
Personally I would always re-install if putting in a new HD. It would seem OS's, I don't know if this is true with Ubuntu but the hardware is detected and set up accordingly. So what is in the compute is not always seem anew by the software.
It could be also be that the computer does not see the drive correctly, and still thinks it is the old unit. I have not had much to do with SATA but they do seem to be a little problematic.
Can I suggest you do a search on the web for like situations. Sorry I can't help further, but your results would be appreciated.

---

