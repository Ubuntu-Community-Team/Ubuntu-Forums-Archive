---
title: "Intel i850 Install OS Issues"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by Epidural on 2008-12-24
When using the LiveCD (on three seperate CDs, so it's not a CD Defect as they have all worked before), I get about 100 errors fly by me and it brings me to a command prompt.

The last few errors I'm given are:

-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied

for about 20 lines.

The same happens when trying to Install from the CD to the HDD.

How can I change the permissions? Is it even a permission error, or is it something else?

Also, each CD has been checked for defects and each has "7 errors on disk", but they each work on other computers with no problems. 

Any theories are greatly appreciated.

---

### Post by Pumalite on 2008-12-24
Clen the lens in your burner or change it.

---

### Post by Epidural on 2008-12-24
> **Pumalite said:**
> Clen the lens in your burner or change it.


I changed burners to a new CD/DVD Writer drive, still same outcomes.

Does it 100% have to be the discs? Because they were all written at different times (about a month apart) and all have worked when they were made as well as several times after. It seems to be only this specific computer set-up which has been causing me problems. 

XP works flawlessly, as much as I hate to admit it, so it's not the drives and/or hardware that are malfunctioning in some way, unless it's something specific to this version of Ubuntu and my hardware.

---

### Post by Pumalite on 2008-12-24
Ubuntu then doesn't like your hardware. Could you post your specs in detail?

---

### Post by Epidural on 2008-12-24
> **Pumalite said:**
> Ubuntu then doesn't like your hardware. Could you post your specs in detail?

The only things that could be throwing off Ubuntu are the CPU, Motherboard or RAM. Everything else came out of a computer that has had and used Ubuntu on it before.

Windows XP Pro works with everything just fine, but Ubuntu doesn't seem to enjoy it.

The motherboard is from Intel but has no markings on it that could tell me what it is. It came from a Compaq Presario 7000, m/n: 7102CA

The CPU is a Pentium 4 1.3Ghz

RAM is RDRAM, the 'Rambus' memory, totalling 768MB (2x 256, 2x 128 )

If there's anything else that you need to know that wasn't submitted, please ask. (: Thanks for your help.

---

### Post by Pumalite on 2008-12-24
Graphics in general is pretty important and the point at which many installations fail. Usually one uses the Alternate CD to avoid problems.

---

### Post by Epidural on 2008-12-24
> **Pumalite said:**
> Graphics in general is pretty important and the point at which many installations fail. Usually one uses the Alternate CD to avoid problems.

Ahh. Just found something interesting. When trying to install a program on Windows XP (to pass some time), it gave me an error message saying "Only part of a ReadProcessMemory or WriteProcessMemory request was completed"

I moved the CD from the DVD drive to the secondary CD/RW drive, and it's working fine.

I'm wondering if, for some reason, my new hardware isn't quite communicating right with that DVD drive and when it hits a certain point, comes up with a similar error when trying Ubuntu. I'm going to switch my Master to the CD/RW instead of the DVD, see if this makes a difference. I'll reply back with the findings.


PS: It's an nVidia GeForce FX 5200 128mb video card, which worked with Ubuntu on my last system.

---

### Post by Epidural on 2008-12-24
AND WE HAVE SUCCESS!

So whatever the hell it is, it's something to do with that DVD drive and loading CDs. 

I'm happy now. I took a huge sigh of relief that I wouldn't have to use Windows to use the internet. =X Dodged a bullet there.


Thanks for helping.. if you happen to know why this might have happened as it did, please post it. If not.. well then we learned something new today, even if we have not a clue as to what happened.

---

### Post by Pumalite on 2008-12-24
I'd say the drive is the problem until proven otherwise; or the connection on the motherboard. Maybe Ubuntu didn't like that it wasn't 2nd Master.

---

