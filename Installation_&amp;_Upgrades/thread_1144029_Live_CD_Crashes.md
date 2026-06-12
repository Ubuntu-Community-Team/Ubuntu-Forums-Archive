---
title: "Live CD Crashes"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by joejvj on 2009-04-30
Hello,

I am trying to install Ubuntu 9.04 on a Dell Inspiron 7500 laptop w/512MB Ram and 30GB hard drive.

I have removed "quiet" and "splash" and here is what happens:

(1) The screen stops at this line for about 5 minutes:
[35.22951] squashfs version 3.3 (2007/10/31) Phillip Lougher

(2) Then it starts to run again, then stops for 5 more minutes at this line:
[158.134598] input SynPS/2 Synaptic Touchpad as /devices/platform/i8042/serio1/input/input7

(3) It starts running again then I see "Segmentation Fault" wizz by, and stops on this line,
[517]232036 EIP:[>c01h880797>] kmem_cache_alloc+0x049/0xb0 SS;ESP 0068:df751ed4

At this point, the whole thing freezes. (Interestingly, plugging in a PCMCIA card or PS/2 mouse displays a line about those devices being added/removed.

I have tried both 8.10 and 9.04 Live CD and both do the same thing. I even tried installing using the alternate installer, and the same thing happens from the hard disk. 

I can boot with Fedora 10 Live, Slax, and Gentoo Live CD's and they all work like a champ. 

I really would rather go with ubuntu, so if anyone can help me solve this I would appreciate it.

---

### Post by joejvj on 2009-04-30
Anyone? I'm a total newbie and need some help!

---

### Post by upchucky on 2009-04-30
not sure how long you waited untill you decided that it was feeezing, I think it is not freezing as the recognition of activity by adding and removing devices says the os id working, try again, be very patient. if no progress after an hour, try the alternate cd for installation, u may have a piece of hardware that is gonna need some settings done after the install completes.

if the live cd booted up to a graphical display before you did an actual install then this proved the machine will be fine with ubuntu.

---

### Post by Old_Grey_Wolf on 2009-04-30
Deleted, more knowledgeable help has arrived.

---

### Post by albinootje on 2009-04-30
> **joejvj said:**
> 
I can boot with Fedora 10 Live, Slax, and Gentoo Live CD's and they all work like a champ. 

Can you try some alternative boot options, like "noapic nolapic" :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You can press "F6" to do so on the Jaunty install cdrom, and with that you can choose more than one option.

---

### Post by joejvj on 2009-05-01
I did let the computer set for at least an hour, and it never came back. I tried various boot options and it didn't change anything. The other live distros I tried did have their problems too, like not recognizing my pcmcia wireless card, etc. They did boot, though. 

Thanks for your replies. I really wanted to run ubuntu on this laptop, but I'm not a "techno-geek" and not smart enough to get this working on my own. Would be nice if there was some step-by-step troubleshooting guides for non-technical people like me. I guess I will go back to XP.

Thanks anyway.

---

### Post by albinootje on 2009-05-01
> **joejvj said:**
> I did let the computer set for at least an hour, and it never came back. I tried various boot options and it didn't change anything. 

Too bad :(
> 
I really wanted to run ubuntu on this laptop, but I'm not a "techno-geek" and not smart enough to get this working on my own. Would be nice if there was some step-by-step troubleshooting guides for non-technical people like me. 

From what you posted it looks like an issue too serious to have a simple howto for.
> 
I guess I will go back to XP.
Why don't you try SimplyMepis, Linux Mint, or another Debian or Ubuntu based Linux distribution before you go back to XP ?

---

### Post by joejvj on 2009-05-01
okay, I will try SimplyMepis and Linux Mint and report back here.

---

