---
title: "No gui after driver install..."
date: 2008-08-15
forum: Hardware
---

### Post by Yooshua on 2008-08-15
So I am very new to Linux! I consider my self a computer savvy person so I want to try it out. I installed Ubuntu on my old box no problem. Booted it up installed all the auto updates. Then I restarted... Everything is working fine.

      So I get home from work today and decided to install the display drivers via the automatic interface. Now I have a big problem. Since installing the new drivers I get no GUI after boot up. I can get to the grub troubleshooting prompt. I get the "unbuntu" logo and progress bar during load up also. After that just a blank screen. Also before the OS even starts loading during the bios loading screen, where it detects the hardware and what not (I don't know what it's called), The screen looks to be about a 1/2 inch offset to the left. So some of the stuff gets cut off (I'm not sure if that started happening before or after the driver install).

      Also I get an message that is displayed by my monitor that says optimal settings are 1600x1050 (the native resolution). So I look at my screen resolution via my monitors info menu and it says that the monitor is set to 1600x1200.

      What I would like to know is there any way I can uninstall/modify the drivers via a command line interface and/or set the resolution to 1600x1050, to see if that fixes the problem?

Hardware specs:
Mobo: MSI intel 865G (neo 2 series)
CPU: Intel P4 2.8ghz (prescott core)
GPU: ATI X800XL (AGP bus, 256mb ram)
ram: 1ghz DDR1 400mhz
Sound: SB Audigy2
Monitor: Samsung Syncmaster 2226BW (connected via VGA cable)
Ubuntu: 8.04.01 - x86 via the liveCD

Thanks for any help!

---

### Post by Liquidtricity on 2008-08-15
This could be a couple of things but the first thing you should try doing is going to /etc/X11/ and using cp to bring you old xorg.conf file back from the dead to replace the new one. as follows ex.
cp xorg.conf.old xorg.conf

If this doesn't work then we'll try some other things.

---

### Post by Yooshua on 2008-08-16
So what do I do to get to that prompt?


and btw... there is no x11 dir under etc.


edit 2... So disreguard the things falling off the screen. I just had to adjust my monitor. It seems to be a problem when I switch from VGA to DVI on my monitor(I use to to swap between puters)

---

### Post by Yooshua on 2008-08-16
deeehy bump

---

### Post by Yooshua on 2008-08-24
So I'm in my etc dir and there is no x11 sub dir... any thoughts?

---

