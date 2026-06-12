---
title: "Acer 5920G Hell"
date: 2011-06-27
forum: Hardware
---

### Post by arendald on 2011-06-27
I have multiple issues with an ACER 5920G and Ubuntu 11.04.

Hardware specs:

- Core2Duo T7100 1.8 Ghz
- 2x2 Gb DDR2
- SATA Drive 500 Gb Seagate
- 8600M GT

After 4 complete installations of 11.04, symptoms are more or less the same:
First message, right after install tells me the system does not meet the hardware requirements to run Unity.
I checked here [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)
It says it's ok. So someone is wrong here. The page or the message. Confusing since both sources are Ubuntu.
Anyway, Unity does not work on my system with nouveau 3D experimental driver.
For the Nvidia proprietary driver, it's another story.
Sometimes it works, sometimes it does not.
Sometimes I can reboot dozen of times or more without any success, stuck (probably) on plymouth. The drive rolls for some time and then nothing. CTRL ALT DEL works or the laptop button On/Off.
Sometimes it works. Then, of course, I thank the god since I have no idea why. GDM is ok with the right rez (1280x800), I even see the nvidia logo before gdm, unity works perfectly (well as perfectly as it can perform). Consoles are ok, right size with right font. The only problem is I never know when it's going to work.
The nvidia driver is the recommended current 270. We're in june and the system is up to date. So far I haven't seen nothing fixing that and frankly I do not expect nothing fixing it since I have some experience with ubuntu distros.

I did try a few things caught here and there on forums, blogs etc. on my previous install but so far nothing works.

So any suggestion, idea, whatever?

I think it's quite sad it doesn't work because the install process was quite nice, the new font ubuntu seems real nice and clean and unity quite promising (but still in dev obviously).

Got a question for the ubuntu guys, why did you release 11.04 with the new unity knowing it only works with a proprietary driver which you do not control at all? IMHO it's wasting a nice piece of code and a very promising 'distro'.

P.S. Btw I have also 'tried' twice to install 11.04 on my main puter based on a Gigabyte X58A UD3R, i7 950, SATA 3 drive, GF 560 Ti. Installations went fine. No error message. No grub. Game over. I think it's a AHCI trouble but not sure. Can't change my bios AHCI settings anyway because if I do W7 is ****** up. It's quite hard to be a linux evangelist these days lol

---

### Post by DelusionalX on 2011-08-31
I have the same issues.

The problem is the graphics card.

The fix? There isn't one.
Ubuntu devs are too busy pushing out new features that nobody likes (Hello Unity) while they lack support for standard features.

I don't think they even know that every Macbook sold a few years ago has the same graphics card AND the same issues. (nVidia GeForce 8xxxM series)

It's sad to see Ubuntu go downhill this fast.
If Oneiric Ocelot also doesn't work with my graphics card, I'm saying goodbye to Ubuntu forever (which is also pretty sad as I'm a translator and am part of a local Ubuntu community).

---

