---
title: "Gigabyte MB, Nvidia. My experience of 15 distro's"
date: 2008-09-09
forum: General Help
---

### Post by ntbutler on 2008-09-09
This is sort of a cry for help if anyone knows how to address this, but also a bit of a warning to anyone thinking of upgrading their system and want to use linux on it.

I have recently upgraded my system, main specs are:
[LIST]
[*]Gigabyte EP45-DS3P motherboard
[*]Intel Quad Core Processor
[*]Nvidia GeForce 8800 GT
[/LIST]

This is a little bit of a heads up to my current experiences with linux since the upgrade.

Ubuntu (Pre 8.04):
Nothing works... I have tried 5.10, 6.06, 7.04 and 7.10 (live cd's where possible) and NONE of them will run (liveCD) or install. There was a mention on one of my previous posts about this that it was possibly because the p45 chipset wasn't properly supported.

Ubuntu 8.04, 8.04.1, PCUser ExtremeOS:
Boots from CD and Installs ok, but it is necessary to have the sata mode in your bios sot to raid to get you anywhere (random thing that just has to be apparently).
I have had issues with all 3 versions with the on-board network card, the RealTek Semiconductor (yadda yadda) ethernet ports work sometimes, thes stop working. Upon inspection, all settings for the connection and port have been set to 0 (or 0's), and i have not been able to resolve this.
I have had issues with the on-board sound card also. Again, seems like a random thing, the liveCD detected the hardware sometimes and sot others... Not so bad, but somewhat annoying.
Lastly, i have had major issues with the system crashing. I believe this to have something to do with the nvidia driver, but noone seems to have been able to help on this subject.
Desktop effects, screensavers, power management (i.e. sleep mode) etc seem to be the main triggers of the crashes, as well as video players.
(I had some pretty funky error log messages about Xorg and other processes being 'Tainted' at the time of the crashes...)

Ubuntu 8.10 Alpha-5:
I just thought i'd try this alpha release to see how things were shaping up for next months release. Didn't boot...

Mandriva 2007:
Didn't boot.

Gnoppix:
Didn't boot.

Mandriva 2008:
Network worked fine, same sound problem.
Graphics card was listed when i ran lshal, but in the graphics and monitor configuration settings, it was listed as vesa, with a vesa monitor (not my dell one).

openSuze 11:
Detected everything fine, but took me too long to try to install the proper nvidia driver for the card (took forever to get all of the dependancies for the installer to build the kernel module, i eventually gave up).

Fedora 9:
Pretty much the same as openSuze, good detection, but installing the driver turned out to be too much of a pain for me.

PCLinuxOS 2008:
Detected the network and the graphics card fine, but no network. Same deal with the nvidia driver, kinda hard to get the installer's dependancies without a network...

Linux Mint (Elyssa):
I am using Elyssa to write this now. Network and sound have been working fine. As usual, the nvidia driver is being a pain (mint apparently doesn't come with all the bits 8.04 has which the installer needs), so when (or if) i get that installed i'll post whether it crashes in mint or not.

__________________

So, I hope that gives you a good idea of some of the problems around, as you can see i have tried quite a few different flavours of linux and out of what i tried, i have to say Mint and openSuze were probably the nicest ones of the lot.

If anyone has any ideas for how to address any of the issues i came accross, please let me know, i am a big ubuntu fan and don't want to give it up, but at least until the 8.10 release i don't really have much choice, no'one so far has been able to identify the problem...

Otherwise, my advice to those with similar specs to me, back up whatever you hold dear, have a stab at it, and if it has issues, try mint or hold out for 8.10.

*rant over...*

---

### Post by Sycron on 2008-09-09
What architecture are you using? A friend of mine has Quadcore too and 8800GT and they all works wonderfully.

---

### Post by ntbutler on 2008-09-09
This is the output of lspci (i think that should tell you just about everything)
> 00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation ICH10 PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation ICH10 PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
05:07.0 IDE interface: Integrated Technology Express, Inc. Unknown device 8213


---

### Post by ntbutler on 2008-09-09
Sorry, forgot to mention that is the output on Mint. I am not sure if that is makes a difference, i'll hunt down and see if i can get the output on my 8.04 boot...

---

### Post by ntbutler on 2008-09-09
Hmm, looks like i never posted it in my last thread...

Being it's nearly 2am i am going to hit the hay for now, but in the morning i will try to get the 8.04 lspci output uploaded. :)

---

