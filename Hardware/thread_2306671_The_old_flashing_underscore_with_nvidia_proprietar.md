---
title: "The old flashing underscore with nvidia proprietary drivers (new twist)"
date: 2015-12-17
forum: Hardware
---

### Post by Qbeta on 2015-12-17
Yesterday, desiring to get some more use from my MSI GTX 960 4G video card I installed the nvidia proprietary graphics drivers. I rebooted and everything seemed fine, great even. Graphics performance had gone from mediocre with the nouveau drivers to pretty awesome. I'm using this system for CAD work for 3d printing so this was pretty important. Upon rebooting yet again, though, I just got a flashing underscore in the upper left corner of the screen. Initially, I thought the hard drive might be corrupted but ruled that out by booting to recovery mode. The new twist on this is that even when booting to my installation USB stick I still got the flashing underscore!! Now the stick just has the basic drivers, which work fine for the install and for running live without installing. My 2560x1600 UHD monitor was detected and that video mode was in use while running live. I started to think the graphics card itself was hosed but everything seems to work fine in Windows 8.1. I'm starting to wonder if the nvidia drivers do something nasty to the card's firmware though Windows seems to tolerate whatever it might have done just fine.

These are the details

**OSes**: Ubuntu 15.10 and Windows 8.1 (dual boot): fresh install of both.

[CENTER]**System Hardware Specs**[/CENTER]

**Video Card**: MSI GTX 960 4G
**Mobo**: ASUS X99-PRO
**Memory**: G.SKILL Ripjaws 4 Series 32GB (4 x 8GB) 288-Pin DDR4 SDRAM DDR4 2800 (PC4 22400) Extreme Performance Memory Kit Model F4-2800C16Q-32GRK
**CPU**: Intel i7-5820K CPU @ 3.30GHz

Nothing is overclocked, the memory works fine and is at the default specs, the hardware is all brand new with no other problems noted under Ubuntu or Windows.

Nvidia drivers I tried: nvidia-352 and nvidia-352-updates (same result with both)

I've tried the various things I've seen here about this that recommend purging the proprietary nvidia stuff and reinstalling the nouveau basic drivers. That hasn't fixed the problem and of course would not explain why the unmodified USB installation stick shows the same blank screen and underscore. I'm willing to try other versions of the nvidia proprietary drivers, move the video card to a different slot, even flash the card's BIOS though what I've read about that is fairly scary sounding and my search last night didn't turn up any sources of the default BIOS to download. Does anyone have any ideas here?

---

### Post by Qbeta on 2015-12-18
Well, my problem is solved! This is a bit of a facepalm for me. I went through a number of things, thankfully not including flashing the video card bios. Finally, in the pit of despair I was sitting at the machine with the system off and glanced at the little red LED on the monitor staring back at me like an evil eye and indicating that it had no signal. Finally, it occurred to me - during the whole time I had been trying new things, installing and removing drivers, and reading posts from others with the same problem, **I HAD NEVER TURNED THE MONITOR OFF AND THEN BACK ON!** I realized that, along with the video card, the monitor had not changed or even been power cycled, unlike the system which had been on and off dozens of times. This might explain why I got the same result from the LiveUSB image (which has only basic drivers) and the installation on the hard drive. I unplugged the monitor, ran an errand (just to let any stray capacitance die away) and came back and powered up the system and monitor. Everything worked fine! I realized that even the Nvidia proprietary driver was likely not really at fault, except that I might need to power cycle the monitor each time I reboot. In a fit of optimism, I reinstalled the driver and now have fast rendering at 2560x1600 on my giant monitor. So I'm back using the nvidia-352-updates package from the Ubuntu archives (driver version is 352.63) 

The monitor, BTW, is one of those oddball Yamakasi 301 Sparta 30" monitors that costs about half what others with the same specs do. It's oddball because they ship with instructions in only Korean (no, this is not a joke), run rather toasty, and are a bit thick and heavy. It's a great monitor and a bargain actually but this may be one of its quirks. Now that I understand this I actually wonder if many of the other people reporting the flashing underscore problem actually just never power cycled their monitor too. Well I hope this helped somebody besides me :)

The moral of this whole story that I'm adding to my rulebook for hardware and driver upgrades is: ***power cycle every goddamn thing in the system completely and restart before you totally trust that everything is really OK!***

---

