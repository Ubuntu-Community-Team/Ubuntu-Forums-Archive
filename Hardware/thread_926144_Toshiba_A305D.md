---
title: "Toshiba A305D"
date: 2008-09-21
forum: Hardware
---

### Post by Rianthas on 2008-09-21
I'm going to be using this thread to post my findings, shortcomings, and help for the newer Toshiba A305D series laptop. Currently, there really isn't any collective thread or webpage offering any help, so I'm going to try keeping as much useful information regarding drivers, settings, in this thread with the hopes many other people will benefit (mainly because setting up several things on this laptop up is a royal pain and everyone loves step-by-step instructions giving them the answer).

I've been using using Linux over the last five years and over the last few weeks, I've started running Ubuntu completely (well, I do have a Windows XP virtual machine on VMware, but I digress), and have had to deal with the headache of getting my wireless card, my video driver, my sound card, and a few Fn (function) keys working.

By the end of this week, I plan to have a working, coherent howto for the Atheros NIC that comes with this laptop, the ATI Radeon X1250 video card, and the Realtek HD sound card. With enough people with more experience and knowledge than me, the future might also include a guide for working hibernate/suspend functions and stable support for OpenGL games (WoW, pretty much) with Compiz.

Unfortunately, I don't have enough time to start working on this guide RIGHT this moment. I'll try working on a howto for the wireless NIC later tonight.

Before I leave, if anyone is looking for a media player, I suggest Banshee, which can be found in the package repo. The media touch keys on the A305 and A305D work out of the box with this program. However, it seems to be lacking global hotkeys, but I'm sure something could be hacked (like a keybind to a terminal command to raise or lower volume).

---

### Post by estamand on 2008-09-21
Rianthas,

Check this site for Toshiba laptop installation info.

[http://linux.toshiba-dme.co.jp/linux/eng/installinfo.htm](http://linux.toshiba-dme.co.jp/linux/eng/installinfo.htm)

Looks likey are doing Ubuntu linux testing on their machines.

From the specs i've seen your A305D seems to be the same as the P300D with just different screen size.

---

### Post by Rianthas on 2008-09-21
It isn't.

---

### Post by estamand on 2008-09-21
Ok.  Good luck.

---

### Post by loadinglinux on 2008-09-24
Excellent Rianthis!  At this point I cannot even get the LiveCD to load on this machine.

Thanks!
LL

---

### Post by Rianthas on 2008-10-03
This is seriously going to take some time before I can get enough working information up.

Basically, it dumbs down to this. The webcam doesn't work. The mic doesn't work. The touchpad is ridiculously sensitive and constantly interprets slight accidental taps as clicks. There isn't any ACPI support and none of the Fn (function) keys work. You can get LCD brightness control if you build the omnibook source, but ONLY brightness. The touch sensitive media control panel at top of the keyboard will work natively with Banshee Media Player, but nothing else. I can only get the alsa 1.0.18rc3 to work with the Realtek HD sound card. 1.0.16 has crappy output levels, even with everything maxed and 1.0.17 doesn't work at all. It keeps coming back with an error while trying to compile the source.

The Atheros wireless card does not work out of the box and you have to download and install the new HAL driver from madwifi to get it working. There are no patched drivers for running any kind of network penetration tools (and my major is computer networking and security) and running in monitor mode kills the ath0 network device unless you either reboot or manually set up the device again.

I cannot get the open source driver for the ATI Radeon video card to work and am forced to use the proprietary driver if I want 3d rendering support. Suspend and hibernate do not work out of the box, and you have to completely recompile your kernel with TuxOnIce support and even then, you have to shut down GDM from the terminal, unload the fglrx driver, and then hibernate or else it'll crash. It'll suspend, but it doesn't resume properly.

Right now, this laptop is not supported enough to use Ubuntu (or otherwise) as a viable, working end-user operating system. The only people that really want to run Ubuntu on this laptop are people that can provide CONSTANT bug feedback and being extremely tenacious about getting the developers to do something to support the hardware in this laptop or people that have enough programming experience to attempt to write patches for several different programs to support the hardware in this laptop.

Unfortunately, I do practically everything with my laptop. I need everything working (especially suspend and hibernate) and don't have the time to deal with the problems that comes with Ubuntu on this laptop. I'll probably spend most of Friday and the weekend switching back over to Windows XP.

@loadinglinux: Make sure your CD drive is set as the first boot device in your BIOS.

---

