---
title: "Custom build hardware suggestions"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by TimmyJ on 2009-09-30
Hey everyone,

I'm currently in the process of choosing hardware for a new ubuntu desktop build and I was looking for some suggestions. I'm a software developer that will use the computer primarily for that purpose. I want something that really burns as far as speed goes and has beefy enough graphics to handle a large monitor and compiz without any slowdows (I don't game though, so overkill on graphics isn't necessary). My budget is around $1000 but anything cheaper that fits the bill is definitely welcome.

If you make a suggestion please try to elaborate on why you are suggesting this particular hardware.

Some of the type of suggestions I am looking for:
-Motherboard + CPU combo: intel vs amd, dual core vs quad core, etc.
-RAM: how much? DDR2 vs DDR3
-Graphics card: I know next to nothing about graphics cards, any tips are welcome
-HD: SSD isn't really an option for me for the time being so I'll probably stick with a 1TB SATA or something similar
-Case: I want something relatively compact (mid-size tower is fine) that is not too flashy and is quiet.

...anything else you think would be useful to know

Thanks for the help!

---

### Post by Littleweseth on 2009-09-30
Pre-note : this is in the wrong forum, as hardware choices have little to do with installation or upgrading Ubuntu. </note>



What follows is personal opinions grounded in my experience building a machine for the same purpose as you, for under $1000 australian (which is WELL under $1000 USD.) ;)

My budget didn't include a monitor (as i already have 2x LCD's), nor any other peripherals. I built my computer to be reliable in operation and to *last*, so I valued reliability over cheapness.

**Case:**
Grab yourself a MicroATX case of some kind; they're easier to stash away/lug around, and cheaper to boot.

Mine is a SilverStone TJ08. It has 2x 120mm fans, front and back, which I find keep everything nice and cool (including your hard drives, which hang in the airflow too - not something I can say about my last case.) It also has a dust filter, which is a Good Thing where I live.

Cool temperatures and less dust = longer-lived components. The case is also aesethically pleasing - very elegant and minimal.

**Processor:**
Intel, please. AMD's latest offerings just match the Core 2 in performance, at a much more expensive price. (The story is different in the budget CPU market segment, but we're not in there.)

You want a Core 2 (the i7 and supporting hardware are too expensive for your budget.) I find a Core 2 Duo E7400 is fast enough, and cheap. Pick the fastest processor you can bear the expense of.

If you do a **lot** of compiling (C,C++ development) you may benefit from a quad core; GCC is one of the few programs I have observed to get a *real* benefit from multiple cores. (GCC with four cores really *is* four times as fast.) Most other apps are only single-threaded, so at the same price you end up with dual cores outperforming quad cores (except when compiling. ;))

**Graphics Card**
I have an ASUS GeForce 9600 card w/ 512MB RAM; it was the cheapest card I could get with dual DVI outputs.

This card doesn't even notice Compiz running, and is powerful enough to play games on (even though you're not going to.)

Basically, any PCI-E graphics card you get is going to be massive overkill for your use, because even my old graphics card (4 years old) was quite happy running compiz.

Therefore, pick *any* PCI-E graphics card, preferably a reliable brand (Asus? Gigabyte?) and with 2 DVI outputs, in case you want a second LCD monitor later.

If you don't actually *need* Compiz, then integrated video is perfectly adequate (and *much* cheaper.) Motherboards with integrated video can be found with dual DVI/VGA outputs, too.

**RAM**
Stock up on RAM : it's cheap! I got 4GB of DDR2 (2x 2GB sticks) for a paltry $80 AUD; 4GB is a good amount (overkill?) for nearly everything. Being able to assign 1GB of ram to virtual machines is very liberating. I haven't ever hit pagefile yet.

As far as DDR2/DDR3 goes : it doesn't really matter. A Core 2 machine will generally want DDR2 (which is cheaper, anyway.)

Have i mentioned RAM is cheap? Cram as much into your computer as it can take; 99% of the time more RAM is the most cost-effective performance enhancer.

**Hard Drives**
If you're not stashing loads of videos/mp3's/disc images, 1TB is pretty damn big and you're unlikely to fill it with work material.

A better investment for a work machine is 2x 500Gb hard drives in mirrored RAID, so you can do online backups. (If you're making a living with your programming, you DEFINITELY don't want a hard drive to die and take all your data with it. Clients don't take 'my hard drive died' as an excuse.)

As far as brands go, Western Digital and Seagate are roughly equivalent in (high) quality. Avoid all other brands, like Samsung.

**Motherboard**
I'm partial to Asus, Intel and Gigabyte motherboards : I've found these brands to be rock-solid reliable.

Grab whatever motherboard fits in your case, and supports all the hardware you want to attach; all the cheap Core 2 motherboards are much the same (they all use the G31 chipset.)

In my case, I chose the Asus P5KPL-CM; this was because it was adequate, cheap, microatx size (for my case), and had serial and parallel ports for my hardware hacking. (Yes, we engineers still use serial and parallel ports to talk to things, mainly microcontrollers.)

It also uses solid capacitors for the CPU power regulation (not electrolytics), so it will never develop 'bulging capacitor death.' Capacitor death isn't so much an issue nowadays, but I didn't want to take any chances. ;)




Hope this is enlightening.
- L.

---

