---
title: "Computer never makes it to Grub"
date: 2008-11-06
forum: Hardware
---

### Post by apothecaryaaron on 2008-11-06
This is probably a very weird coincidence, but it only happens with Ubuntu on my desktop.  (ASUS P5ND-SLI mobo, 1 Gb Ram, Pentium D).  When booting, both cold and restarts, it stops on the ASUS mobo splash screen.  
 
I can get into BIOS setup only if I am pressing the button rapidly when I hit the switch.  No changes in there need to be made, and none make a difference when I tried just out of frustration.
 
After many retries I eventually get Grub to appear and from there out Ibex starts wonderfully.  I usually end up opening the case and verifying all connections are good (RAM, SATA cable, Graphics card, etc.).  I cannot find that anything makes a difference, it is purely a random restart gets momentum and makes it through.  
 
It sounds like a hardware issue or something, but it happened absolutely 0 times when I was running Arch.  Anyone have any suggestions or something to test to get more info?

---

### Post by cariboo on 2008-11-06
Have you tried clearing the bios? There should be a jumper on the motherboard right close to the battery.
Have a look here for an example:

[www.teamplayinc.com/Tech/BIOS%20Reset.pdf](www.teamplayinc.com/Tech/BIOS%20Reset.pdf)

Jim

---

### Post by apothecaryaaron on 2008-11-07
> **cariboo907 said:**
> Have you tried clearing the bios? There should be a jumper on the motherboard right close to the battery.
Have a look here for an example:
 
[www.teamplayinc.com/Tech/BIOS%20Reset.pdf]("http://www.teamplayinc.com/Tech/BIOS%20Reset.pdf")
 
Jim
 
Thanks for the reply.
Haven't tried that but I will.  This is not my work computer, so I'm up for about anything on this.  I just really didn't know where to start.  I had forgotten all about it until I put Ubuntu back on it.  I am just hoping it's a hardware cause so that I can just replace a part.

---

### Post by apothecaryaaron on 2008-11-07
> **ilkolinux said:**
> it probably is some hardware issue, but hope its not your hard disk so you dont lose your data.
It's a fresh install, I'll just lose the updates.
Last time it happened I had a different hard disk in it, so I'm making the assumption it's not that.  Linux isn't a space hog like Windows, so I stuck a 40 gb drive in it and used the 160 gb for a home server.  The 160 gb was the drive that acted up before (Gutsy install).

---

