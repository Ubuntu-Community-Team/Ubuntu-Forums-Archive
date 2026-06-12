---
title: "Nvidia tearing, ACPI error and USB Over-Current"
date: 2015-10-10
forum: Hardware
---

### Post by Sh4rX on 2015-10-10
Hello, I am new to the Linux and Ubuntu world ):P Although I have been working with computers for the last 15 years, I installed yesterday Ubuntu 15.04 on my laptop, but despite my efforts I finally surrendered to a few problems that I am not able to solve myself :( To make this easy to read, I am going to split this in more parts.

The hardware:
ASUS K53SC
-Intel Core i7 2630QM @ 2.0 Ghz (2.6 Turbo Boost all cores active, 2.9 Single Core active) 8 Threads 4 Cores
-Nvidia GT 520MX 1 GB DDR3 @ 64 bit, 48 CUDA cores / Intel HD Graphics 3000 
-4 GB DDR3 RAM @ 1333 Mhz
-Samsung 640GB 5400RPM HDD

The software:
-UBUNTU 15.04, installed with all the fancy checkboxes (third party and automatic drivers)
-Nvidia proprietary drivers 346.96, which, for some reason, were not installed by default (nouveau drivers were)
-NOTHING to simulate Optimus or anything similar to that piece of junk, I ONLY want to use the dedicated card, not fast, but still better than the Intel one

The problems:
-ACPI error on boot
-Over current condition on all USB ports (the laptop has one USB 3.0 on the left, directly connected to the motherboard, and two USB 2.0 ports on the right, managed by a controller) on boot
-Tearing that happens everywhere, most noticeable on YouTube videos (wasn`t able to reproduce it in VLC with VPDAU, or at the very least, is not as noticeable as it is elsewhere)

Tried solutions:
-None tried for the boot errors, boot procedure takes a full 60 seconds because of the errors, which is ridiculous... I can live with it though, I have not even looked for any solutions.

Regarding the stupid GPU I have tried so many things that I almost forgot what I did... Anyways, I tried the following:
-Searching for the sync to vblank option, which is NON EXISTENT on XServer GUI
-Switch to Maximum Performance mode (which is done automatically via a startup command, anyway)
-As it is most noticeable on browsers, I tried messing with their hardware acceleration settings. Firefox stutters on 60 fps with it enabled and still tears, Chrome does not even support it yet it still tears. Not related to hardware acceleration
-Glxgears gives a ridiculous 2500 fps... So the issue is definitely Vsync
-Tried using Intel from XServer instead of Nvidia.

Now I am definitely UPSET and SAD and wonder why an option such easy to implement and so useful is not enabled by default and requires hours of pulling hair... I absolutely LOVE this OS, and I feel the need to detach myself from Windows, I have tweaked so much this little baby and made it mine that I`d feel rather angry to just give up on it because of an option that has been on EVERYTHING since at least the year 2000 and is not there on an OS that aims at killing proprietary OSes or whatever.

---

