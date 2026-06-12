---
title: "HELP: completely dead after upgrade"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by timswait on 2009-05-13
I just upgraded to 9.04 from 8.10, all installed, it got to the restart, but now it doesn't work at all. Get the GRUB boot screen, then an Ubuntu logo, the bar fills up, when it gets to the end the screen briefly goes blank and then displays a load of rubbish and just sits there. The rubbish includes a low quality, sort of magenta and cyan version of the ubuntu logo off to one side, some red sploges across the top of the screen and a sring of characters which vanishes off the side of the screen that looks like the mother board name. What can I do, is there any way to go back to the previous version?

---

### Post by sir_nasty on 2009-05-13
from the grub menu try selecting the ubuntu version of "sage mode" and see if that will boot....

sounds like a video issue to me.

---

### Post by Geekkit on 2009-05-13
> **timswait said:**
> I just upgraded to 9.04 from 8.10, all installed, it got to the restart, but now it doesn't work at all. Get the GRUB boot screen, then an Ubuntu logo, the bar fills up, when it gets to the end the screen briefly goes blank and then displays a load of rubbish and just sits there. The rubbish includes a low quality, sort of magenta and cyan version of the ubuntu logo off to one side, some red sploges across the top of the screen and a sring of characters which vanishes off the side of the screen that looks like the mother board name. What can I do, is there any way to go back to the previous version?


This is exactly what's happening to me.

---

### Post by timswait on 2009-05-13
> **sir_nasty said:**
> from the grub menu try selecting the ubuntu version of "sage mode" and see if that will boot....

sounds like a video issue to me.
I think you're right, I'm pretty sure it is a video issue. I've got ATi graphics onboard on the motherboard, and Ubuntu's never been quite right with it. I've never had visual effects working and sometimes when I install updates I get problems with it. However these problems usually make it start in low graphics mode, so at least I can sort it out, but now it doesn't give the option to start in low graphics mode, is there some way I can force it to? Recovery mode does work, I've tried the "auto repair graphics problems" option and that doesn't work, so what else can I do from there?
I've also tried a live CD of 9.04, and that also has the same problem.

---

### Post by cariboo on 2009-05-13
Have a look ath this wiki [page]("http://wiki.ubuntu.com/X/Troubleshooting/BlankScreen"), to see if the troubleshooting tips help you solve your problem.

---

### Post by timswait on 2009-05-14
I've had a look at the that. The screen is not completely blank, but it also doesn't show "Out of Range". As I say it just displays a mangled mess. I've tried connecting it on analog and DVI cables and it makes no difference. I've tried editing my xorg.conf to include the vesa driver, but that doesn't help so I've changed it back again. 
I would try changing the resolution as in this page: [https://wiki.ubuntu.com/X/Troubleshooting/Resolution]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution"), but I don't understand what it means by "In your ~/.xprofile add a line to specify a safer resolution". What is my xprofile? Is this a file, where can I find it? Is there any way to force it to boot in low graphics mode? That's what it's always done in the past when there's been a problem.

---

