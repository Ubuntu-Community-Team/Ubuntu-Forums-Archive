---
title: "Is there a problem with my hardware?"
date: 2010-06-13
forum: Hardware
---

### Post by Jekshadow on 2010-06-13
I'll start with the background story. I got my laptop about a year and a half ago, and it came with Windows Vista. Within 2-3 weeks of getting the laptop, I started to have strange issues, such as explorer.exe would freeze whenever I right clicked and sometimes it refused to start at all. Within a month, it had escalated to giving me BSODs whenever I started it up. I finally stopped trying to fix it and just installed Ubuntu 8.04. That seemed to fix the problems, but after about 2-3 months of using it, programs started randomly freezing, and they seemed to cause a chain reaction. Once one program froze, they all would freeze. At first I thought it was a problem with the kernel or the GTK libraries or something, so I upgraded to 9.04 and the problems kept occurring. I looked at the dmesg and found a long string of ATA read errors, so I swapped out the hard drive for another one I had laying around and installed a fresh copy of 9.04 side by side with Windows Vista. Again, Vista started to have problems, so I deleted the Vista partition and expanded the Ubuntu partition to fill the entire drive. Everything was working for a while, but I decided to try Fedora 13 KDE, and wiped my HDD and installed it. I started noticing that it would randomly freeze, for no apparent reason, so I installed Ubuntu 10.04 last weekend. I noticed that applications were starting to randomly freeze again, so I checked the SMART status (just fine) and checked the dmesg (nothing about drive errors). Applications randomly freeze, and, like when my hard drive was failing, caused a chain reaction of freezing applications.

I have a Dell XPS M1330, and I would not be surprised if there was a problem with the hardware. My dad had to swap out everything but his case, WiFi card and screen out of his M1210 because it ran too hot and I have had to put a bag of ice under mine several times because the aluminum on top was easily over 100F when the room temperature was only ~70F.

---

### Post by wojox on 2010-06-13
Sounds like your graphics card/chip. Did you see anything in your logs about that?

---

### Post by Jekshadow on 2010-06-13
> **wojox said:**
> Sounds like your graphics card/chip. Did you see anything in your logs about that?

Nope, I see nothing in my syslog, dmesg or kern.log about my graphics card, other than my kernel complaining about how the nvidia module taints the kernel.

---

