---
title: "Any reason for this not working?"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by weirdalex on 2009-02-05
I have tried ubuntu & kubuntu 8.04 & 8.10 and the same
thing happens when booting the live cd. Just as the desktop
begins to finish, the taskbar is all garbled, and the PC is locked up. :confused:
I cannot install the distros mentioned above, as well as Fedora core 9 or 10 - OpenSuse 10 or 11. Seems *nix in general will not
go onto this system.
I did google compatibility with all hardware, with results coming back as "fully supported" to "minor issues (solved)", and tried those workaround/fixes.

I myself have tinkered with *nix starting back at Redhat 6.0 and am currently, successfully running Ubuntu (8.04) on an Intel-based system. I've built my own systems since 1996, so I am no beginner, nor do I claim excellence in my knowledge.

```
**System Configuration:**
**Mainboard:** Asus M2N-SLI Deluxe 
**CPU:** AMD Athlon 64 X2 Dual Core 5200+ (Windsor)  @ 2.61 GHz 
**RAM:** G. Skill 2x 2048 GiB (4096 GiB) DDR2 800 
**Video:** eVGA nvidia 7800 GT (x2) SLI (or not SLI)
**Hard Drive:** Western Digital WD50 00AAKS-65A7B ( 3.0 GB/s 500 SATA GiB HDD) 
**Optical Drive:** Asus DRW-2014L1T SATA DVDRW
* System is **NOT** overclocked *
```

Any/all help is greatly appreciated. :)

---

### Post by hyper_ch on 2009-02-06
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Dies on 2009-02-06
> **weirdalex said:**
> I have tried ubuntu & kubuntu 8.04 & 8.10 and the same
thing happens when booting the live cd. Just as the desktop
begins to finish, the taskbar is all garbled, and the PC is locked up. :confused:
I cannot install the distros mentioned above, as well as Fedora core 9 or 10 - OpenSuse 10 or 11. Seems *nix in general will not
go onto this system.
I did google compatibility with all hardware, with results coming back as "fully supported" to "minor issues (solved)", and tried those workaround/fixes.

I myself have tinkered with *nix starting back at Redhat 6.0 and am currently, successfully running Ubuntu (8.04) on an Intel-based system. I've built my own systems since 1996, so I am no beginner, nor do I claim excellence in my knowledge.

```
**System Configuration:**
**Mainboard:** Asus M2N-SLI Deluxe 
**CPU:** AMD Athlon 64 X2 Dual Core 5200+ (Windsor)  @ 2.61 GHz 
**RAM:** G. Skill 2x 2048 GiB (4096 GiB) DDR2 800 
**Video:** eVGA nvidia 7800 GT (x2) SLI (or not SLI)
**Hard Drive:** Western Digital WD50 00AAKS-65A7B ( 3.0 GB/s 500 SATA GiB HDD) 
**Optical Drive:** Asus DRW-2014L1T SATA DVDRW
* System is **NOT** overclocked *
```

Any/all help is greatly appreciated. :)

Your specs are very, very similar to mine, I have 7600's. Those distros should all work.

Is it actually locked up, or can you switch to a terminal?
Have you tried pulling one of the graphics cards? This can sometimes cause issues until you specify a BusID for the primary card in xorg.conf.
If you can get to a terminal then you can edit it in and restart X.

Also, what bios version are you running? In my case, when I updated the bios no install would work, not Linux, not Windows, not BSD, not anything. Luckily I saved the original - bios 0202.

Does a Windows install CD boot succesfully?

Another thing is memory, and how picky this particular board can be about it. G. Skill is not on the QVL so maybe swap it with the memory from your other system just to make sure that's not the cause.

---

### Post by weirdalex on 2009-02-06
BIOS ver. 1502
Windows XP, Vista and Windows 7 all install flawlessly.
All of my DDR2 is G. SKill, heh...maybe I should've bought something else.

---

