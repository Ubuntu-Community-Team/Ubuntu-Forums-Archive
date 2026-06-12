---
title: "ATI 6520G (integrated VGA) and 6600M (dedicated VGA) using radeon open source driver"
date: 2015-09-30
forum: Hardware
---

### Post by cricokiss on 2015-09-30
**Good afternoon.**

I have a ASUS N53TA laptop which comes with two video cards:
  * ATI 6520G (Integrated)
  * ATI 6600M (dedicated)

I'm using the open source driver called "radeon" and it's running most of my games and applications pretty well (better than the proprietary driver "fglrx", by the way). I usually play simple games and high performance isn't always that important.

However I'm getting choppy performance on more complex games such as Left 4 Dead 2 (about ~20 fps). The bad performance makes me thing that I'm not using my dedicated video card, only the integrated one.

Since I don't think it's an issue related to the game itself, I'm asking here if there is any additional configuration that I must set to use both video cards on 3D applications.

I would not ask here in the official forums if I didn't search enough. Here are all the things I've already tried:
  **1. Installing the proprietary driver:** bad performance on simple games and unstable frame rate on more complex games. I've heard that "fglrx" does have its problems with Linux, so I'm using the open source one.
  **2. Looked for a way to enable crossfire:** it seems that crossfire isn't working properly with the open source driver (see [http://www.phoronix.com/scan.php?page=news_item&px=MTYxNjM](http://www.phoronix.com/scan.php?page=news_item&px=MTYxNjM) and [http://www.phoronix.com/scan.php?page=news_item&px=MTQzNjE](http://www.phoronix.com/scan.php?page=news_item&px=MTQzNjE)). The crossfire seemed like a good option because this notebook does use both video cards to increase performance on demanding applications (I still have my doubts about ASUS properly doing crossfire between integrated and dedicated VGAs, but I guess this is off-topic).
  **3. Looked for a way to enable only the dedicated VGA:** I didn't find anything about this possibility. Again, my PC is working fine with most of my applications, so I want to use the full performance only on applications that are really necessary.

[B]Additional information:
[/B]
  1. Left 4 Dead 2 runs fine on Windows 10 using Catalyst 15.7.

    2. Command "**sudo lshw -c video**" lists only the 6520G video card:
  *-display               
       description: VGA compatible controller
       product: BeaverCreek [Radeon HD 6520G]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff

**Thanks in advance.**

---

### Post by QIII on 2015-09-30
What you have heard about AMD is wrong.

When you installed fglrx, did you do
```
sudo amdconfig --adapter=all --initial 
```

before rebooting?

That will configure both adapters and likely improve performance.  Catalyst Control Center will allow you to switch between them.  However, the switch is not on the fly like Windows.  You have to reboot.

---

### Post by cricokiss on 2015-10-01
Thank you for your response.

I didn't know about that command. I'll try it out and post the results here.

---

### Post by cricokiss on 2015-10-02
[COLOR=#383838][FONT=gotham]Hello.[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]
Yesterday I've tried again to use the fglrx driver from AMD. After installing the drivers and running the command suggested by QIII, I had the same problems as before:[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]
[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]  * Uneven frames per second on 3D games. Left 4 Dead 2, for example, runs at ~45 fps but sometimes it goes to 100 fps and then suddenly drops to 10 fps. Another game, Trine, runs a bit better with the proprietary driver, though.[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]  * Choppy performance on simple games such as World of Goo, Super Meat Boy etc.[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]  * Wine freezes when trying to run some old games.[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]  * Strange noise in the fan.[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]
[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]I didn't revert the driver installation yet, but it seems that my hardware isn't properly supported by AMD anymore.[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]
[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]It's important to mention that I followed these instructions, which does have the command above suggested by QIII: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]
[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]Some additional information that may help:[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]
[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]  * I'm using Ubuntu 14.04 x64.[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]  * I've installed the VGA driver from "Additional drivers" inside Ubuntu settings. I remember I saw somewhere that the installed version is 15.20.[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]  * Windows 10 also doesn't run well with the latest Catalyst driver. It takes about 1 minute and a half just to show the login screen, which remains black until then. This issue seems to happen quite a lot in Windows 10 with ATI users, specially with mobile cards. Black screens also occur when changing resolution between applications. Since both Microsoft and AMD ignored my emails about those problems, I decided to use my Ubuntu partition for gaming as well (90% of my games are MS-DOS or 100% Wine compatible). I'm quite impressed with the results, since everything runs pretty fast on Ubuntu.[/FONT][/COLOR]

---

