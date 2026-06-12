---
title: "Unable to install xubuntu on laptop, need help!"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by brackenan on 2009-07-27
Here’s what keeps flashing across the screen while loading…
   
  [272.854943] ata2.00: status: {  DRDY ERR  }
[xxx.xxxxxx] ata2.00: error: {  UNC  }
[xxx.xxxxxx]ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[xxx.xxxxxx] ata2.00: BMDMA stat 0x25
[xxx.xxxxxx] ata2.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in

the x's are all different numbers. The message repeats several times. Sometimes it says:
   
  [400.467392] Buffer I/O error on device sda1, logical block 19537685 (<this number changes as it keeps scrolling across the screen) 
  ^ (this number also changes)


After it's all done with this, it loads into the dialog boxes fine, but when it gets to partition box, it doesn't show a hard drive.  I know this drive is fine, runs xp like a champ.


I've heard enabling the acpi=off and eed=on command on boot screen would solve this problem, but it still does the same thing and the last time I tried it, it just shut down on me! 

   
  I’m stumped…
   
  It’s a Dell Latitude CPx, w/ Pentium III 750MHz cpu


Any help would be greatly appreciated!  I'm not that new to Linux, but don't know alot about the commands and the real technical parts of it.  I'm currently self-employed as an IT Technician, so I'm quite familiar with computers.


Thanks in advance!


Andrew

---

### Post by running_rabbit07 on 2009-07-27
Have you tried the check disk option?

How much RAM do you have?

Does the disk boot in the Boot Without Making Changes to Your System Mode?

---

### Post by brackenan on 2009-07-28
I finally figured out the problem.  Turns it was a bad hard drive, which really surprised me considering I bought it no more than 4 months ago!  Anyway, I pilfered a HD from another computer where I work and I had no more errors, and it booted from the Live CD perfectly.  

I have 256Mb (2x128s) of RAM installed and for some reason the second RAM channel works intermittently.  Sometimes you boot it up and its fine, others, it won't recognize it.  Seems like the mobo is messed up. But, I just bought a 256 stick to replace both 128s.  So at least one channel works lol!  Thanks anyway for your help!

Andrew

---

### Post by running_rabbit07 on 2009-07-28
> **brackenan said:**
> I finally figured out the problem.  Turns it was a bad hard drive, which really surprised me considering I bought it no more than 4 months ago!  Anyway, I pilfered a HD from another computer where I work and I had no more errors, and it booted from the Live CD perfectly.  

I have 256Mb (2x128s) of RAM installed and for some reason the second RAM channel works intermittently.  Sometimes you boot it up and its fine, others, it won't recognize it.  Seems like the mobo is messed up. But, I just bought a 256 stick to replace both 128s.  So at least one channel works lol!  Thanks anyway for your help!

Andrew
  Stupid question, have you tried blowing out the slots with compressed air?

---

