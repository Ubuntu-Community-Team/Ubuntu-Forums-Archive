---
title: "X1600 with fglrx produces strange problems"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by Monkey358 on 2006-11-14
Running Kubuntu 6.10 Edgy Eft, on an Athtlon XP 2GHz 32-bit, 512MB DDR400 RAM, normal IDE drives, 2 hard drives, 2 optical drives. It has an ATi Radeon X1600 Pro in the AGP-8X slot and no matter what I do, I can't get the binary ATi driver working, and I'd like to use Beryl with KDE.

If I install the drivers via apt-get, or building them manually, it works, but the DRI is disabled, so I go and add the bit to my X.org about disabling Composite, restart the computer and all hell breaks loose.

The images rendered don't erase unless rendered over by something else, makes the system entirely unuseable, I've attached a screenshot with Konsole, Ksnapshot, and Firefox running. Also, the kicker bar doesn't load entirely.

---

### Post by Monkey358 on 2006-11-15
Shameless bump, I need this computer working.

---

### Post by zo_here on 2006-11-19
Same problem here.
I'm sorry that i cannot help you - but if you find an answer, could you post it, please?

btw, sounds stupid, but i'm feeling a little bit better about not being the only one with that bl**dy problem :(

---

### Post by Monkey358 on 2006-11-20
I solved the problem by resetting my BIOS AGP settings to default.

---

### Post by zo_here on 2006-11-20
ok - thanks for the message! i'll try this tonight at home.

---

### Post by Monkey358 on 2006-11-20
I sacrified my system and 're-broke' it and played around, it seems to be related to the AGP aperature size, too small and bad things happened.

---

### Post by zo_here on 2006-11-20
Argh - no chance here. I've set the bios to the factory-defaults - no change. Tried different kernel-variants (agp as module to use the ATI-agp-mode, different memory-settings etc.) - no change. Changed even some setting of some related jumpers on the mainboard (which i never do... i don't like to move atoms :D ) - no change.
I really tried everything i could think of - no change. Either i cannot use 3d-accel with my X1600, or there are those bloody artefacts with the redraw.

At the present moment, i guess it is something between the ATI-card and the mainboard-settings. The machine is not a really new one, and the AGP-slot is not a 8x-one. I don't get any error-messages in the logs - neither in the xorg-logfile nor in syslog, so i don't think it's a software-problem - but hey, who knows... :(

Have you found a setting in your BIOS that really worked with your card?

---

### Post by Monkey358 on 2006-11-20
Like I said, I got most results with the AGP Aperture Size settings at 512MB for the AGP slot, but I'm running 8x, try a lower number?

Also, try a factory reset on the mainboard settings?

---

### Post by zo_here on 2006-11-21
Ok, thanks.

Problem is: I already tried the factory defaults of the mainboard. The one I use is only capable of 4x AGP, and in the BIOS-settings, i can give it a max amount of 64MB RAM.

That board might just be too old for the GPU.

I'll try another tricks on the board and in the software and will then (if nothing works) go to a friend of mine who has a newer mainboard. If the card works there, I'll go and just buy a new board.

But thanks for the help!

---

### Post by Kurzweil on 2006-12-09
Thanks so much for this! I've been fighting this thing for days but moving that up seems to be working. I could only move mine to 256 for somereason though but its working anyways! :-D  When I load up an xgl sesson to run beryl windows seem to open very slowly.. Like 4 and 5 seconds to open a terminal, but the effects in beryl are working ok.Any ideas? This is my last hurdle to deleting windows. lol

---

### Post by kellemes on 2007-03-19
I have x1650PRO

I've been fighting this issue for a long long time..
The AGP Aperture Size settings did it!!!!!!!!

Guys.. I think I love you..

Correction.. I'm sure I love you \\:D/

---

