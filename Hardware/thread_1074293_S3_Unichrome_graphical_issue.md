---
title: "S3 Unichrome graphical issue"
date: 2009-02-19
forum: Hardware
---

### Post by dodle on 2009-02-19
I've seen a lot of talk about the S3 Unichrome integrated graphics, but haven't read anything about this yet.  I'm actually not sure how to describe it.  I have tried using the following drivers to fix this issue: openchrome (current), via, s3, savage, and vesa.  But nothing seems to help.  Everything runs smooth and happy except that I get random... artifacts?  At no particular time the picture goes wacky like someone took a washcloth and wiped the screen, smeering everything that is displayed (kind of like the smudge tool in a paint program).  Well something like that.  Menu icons and buttons disappear from the panel (the reappear when I move the mouse over them).  I'll see if I can get a screenshot.  I'm assuming this is an issue with the graphics processor.

Ubuntu 8.04 (happy with it, Intrepid does not boot up)
Averatec 3280 Notebook
1.6 Ghz AMD Mobile Sempron
512 mb ram
80 gb hard drive
Synaptics Touchpad
Some kind of Realtek AC'97 sound card
any other info needed?

lspci:```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```

**Edit:** Can't get a snapshot, the screen fixes itself when I hit "Print Screen".

**Edit: Edit:** I read that some others were having 3d issues with this card.  So I tried running a 3d screensaver and the machine froze.  Could this be a result of the same issue?

This is as of a screenshot I can get right now:

---

### Post by 00b00nt00 on 2009-02-19
I have the very same chipset in my laptop (K8N800). I can't get Ubuntu to work either, unless it is using the VESA driver. I think the best thing to do is wait for the official release of Jaunty and pray for a miracle.

---

### Post by overdrank on 2009-02-19
dodle have you tried looking at the amount of memory shared with the graphics in the bios. If you can increase this it may help with the issues. Some bios is restricted to the amount of memory added and adjust with the additional memory added. 
Also have you tried the command with the alt, F2 keys ```
gksu displayconfig-gtk
``` and adjust.

---

### Post by dodle on 2009-02-19
> **00b00nt00 said:**
> I have the very same chipset in my laptop (K8N800). I can't get Ubuntu to work either, unless it is using the VESA driver. I think the best thing to do is wait for the official release of Jaunty and pray for a miracle.

Are you trying to install 8.10?  I couldn't get it to work either.  I had to install 8.04.

> **overdrank said:**
> dodle have you tried looking at the amount of memory shared with the graphics in the bios. If you can increase this it may help with the issues. Some bios is restricted to the amount of memory added and adjust with the additional memory added. 
Also have you tried the command with the alt, F2 keys ```
gksu displayconfig-gtk
``` and adjust.

I have been messing with displayconfig-gtk with no positive results.  I'll see what I can do in the bios.

**Edit:** This mobo's bios has very few options.  There is one called "Share Memory" but it's at its max: 64mb.

---

### Post by dodle on 2009-02-20
Solved with the vesa driver.  Apparently when I used displayconfig-gtk, the configurations weren't saving to xorg.conf.  So manually input the settings and the screen works great with vesa.  Luckily this laptop is small and I don't need resolutions higher than 1024x768.  The graphics card isn't very powerful, but vesa still gives me some 3d functionality.

Thanks for the help on this subject.

---

