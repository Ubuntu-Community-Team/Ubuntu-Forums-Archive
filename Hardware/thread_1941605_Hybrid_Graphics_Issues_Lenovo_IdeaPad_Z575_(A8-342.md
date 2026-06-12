---
title: "Hybrid Graphics Issues: Lenovo IdeaPad Z575 (A8-3420M/6550M)"
date: 2012-03-16
forum: Hardware
---

### Post by gdea73 on 2012-03-16
New Post:
 
I spent some time, to solve a glitch, since I was thus involved,
I wrote a [guide](http://ubuntuforums.org/showthread.php?t=1942151) on my new fix; on-the lap-top I just bought.
And since it worked for me, I thought; Then why not mark it [SOLVED]. :D

---

### Post by gdea73 on 2012-03-16
In case you were wondering, the purple screen was the color of the splash, was very blank, and the system basically hangs from there. I could neither switch to a virtual terminal nor reboot with Ctrl + Alt + Del.

---

### Post by gdea73 on 2012-03-16
I would really appreciate any help here; I need as much as I can get. I have been searching the Web for answers about Hybrid Graphics on AMD APUs, with Linux, and have found absolutely no solution. Thanks in advance.

- gdea73 -

---

### Post by UltimateCat on 2012-03-16
If it were me I would want the integrated chip to be usable also-

I am wondering if changing the clock speeds of the card to your chipset would help? In other words you could under clock or slightly overclock.

This book has helped me a great deal in understanding, hardware, chipset's , system BIO's and Graphic's BIO's. "Upgrading And Reparing Pc's" By: Scott Mueller

I am not certain yet but there may be a way to solve the problem w/o falling back to a older version of your kernel.  If I find the answer I will post it under " Hybrid Graphics Solved" (sometimes it is difficult to find a thread)

There are other members in this forum that are very knowledgeable so hang in there;)

---

### Post by UltimateCat on 2012-03-16
Just spent a little over an hour looking through articles and going to websites.....

I've never had this much trouble helping someone.

I did find Hybrid Graphics in an Ubuntu article:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

I even searched in the Linux forum and couldn't find anything so I asked about another way besides you having to fall back into a earlier version of your kernel.

Don't bother going to "Radeon" radeon.com is all about technology but doesn't offer much in or on the subject at hand....I already tried.

This has me perplexed as it is in my nature to help-

---

### Post by gdea73 on 2012-03-16
Thanks for trying to help, I really appreciate it. I would consider underclocking the card for power consumption purposes, or maybe undervolting it, but my proprietary BIOS wouldn't allow it, and Catalys doesn't have OverDrive on Linux. Well I don't know if falling back to 2.6.35-22 would help; I'm on 2.6.35-32 right now, and it didn't work any better on the previous kernel.

I saw that Wiki page too, but it referred to hybrid graphics between Intel onboard and nVidia/ATi discrete GPUs. My setup, "hybrid graphics," as well - is actually an APU which is supposed to "work together" with the 6550M. They are both AMD adapters and as such both use Catalyst, so I can't "switch" drivers altogether.

The current situation is, I get a purple screen on boot with "amdconfig --inital," every time. If I delete xorg.conf, I can get the PC to boot, but then I can't run Catalyst because it's using the open source Radeon drivers. **If I go into BIOS, disable the Radeon HD 6550M (discrete chip), and reboot, I can run on the integrated chipset seemingly fine.**

the issue with this is, (1) it's not fun to have to switch it in BIOS; rebooting is pain enough; and (2) when I turn the graphics back to hybrid mode in the BIOS, I get a purple screen.

So now Catalyst is stuck in APU-only mode, and the only way I can boot with fglrx enabled is if I boot with the APU only, so there's no option to switch back to the discrete card. Hmm... The confusion continues.

Anyone else willing to jump in here? I know I'm not the only one ever to try running Linux on an APU with hybrid GFX :P (though it's starting to feel that way...)

---

### Post by UltimateCat on 2012-03-17
I talked to a member at Linux that helped me with a graphics issue before.
He explained:
" By default the GPU should work just fine if there are no proprietary drivers installed for the AMD GPU.  No need to use an older version of the kernel" ; he said-

Hope this helps and 
Happy Saint Patricks Day
Sincerely,

UltimateCat

---

### Post by gdea73 on 2012-03-18
right, it's true that the GPU *worked* without extra drivers, except the discrete (power-hungry) one was used by default, and 3D acceleration didn't work, so it was basically a more power-consuming version of software rendering, which is not good :P

Thanks for your input though, ;)

---

### Post by UltimateCat on 2012-03-21
Your Welcome!

---

