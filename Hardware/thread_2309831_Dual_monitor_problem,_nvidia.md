---
title: "Dual monitor problem, nvidia"
date: 2016-01-13
forum: Hardware
---

### Post by tuffmcguff on 2016-01-13
I am fairly new to Ubuntu; I've been using it less than a year. I'm fairly computer literate but not great with linux.  I have two monitors, and am having trouble getting them both to work.  I just moved, and they both worked just fine before the move, now they don't, and I have no clue why.  It's not hardware related as I have tried multiple cables, and different configurations of where I'm plugging monitors into, etc... so I am 99.9% certain it's not faulty hardware.

I am running Ubuntu 14.04, have a Nvidia GF119 (GeForce GT 610) graphics card, and an Asus Z97-A-USB31 motherboard.  I have a VGA cable going into my graphics card, and a DVI going into my motherboard, the same as it was before the move.  The only monitor that works at this point is the one plugged into the graphics card.  When I boot, everything in the system seems to be the same as it was before the move, aside from the monitor issue.  So I tracked down one issue to the BIOS; I changed the bios setting "CPU graphics multi-monitor" from "disabled" to "enabled."  The motherboard does not look for onboard graphics if it detects a graph card, but this setting tells it to accept both.  After a reboot, both monitors are displaying text, but now the one that is plugged into my motherboard streams pages of text too fast for me to read, and ends up at the tty1 screen.  I can fully access the system and all files within from the tty1 screen, but cannot get a GUI to display.

I tried:
 sudo xstart
sudo start gdm (it was already running)
reinstalling unity
reinstalling gdm
alt+ctrl+F1
Messing around with all the settings in the bios that have to do with graphics, hoping that some combination will make both monitors display a gui.  No luck
Some other stuff that google recommended that I don't remember.

I can force the computer from the bios to use the onboard device as the primary monitor, and when I do that the Ubuntu splash screen comes up on the monitor plugged into the motherboard, but then it goes black with a blinking cursor in the top left, and is not responsive to anything.

If I change the bios option "CPU graphics multi-monitor" back to "disabled" it boots just fine, and only displays on the monitor connected to the graphics card.


I am really confused and frustrated on this and wish to avoid a format if possible.  Does anyone have any suggestions as to what may be causing this, and how I might fix it?

Thanks,
Bill

---

### Post by john417 on 2016-01-14
Have you installed the Nvidia drivers?

---

### Post by tuffmcguff on 2016-01-14
Yes, and uninstalled and reinstalled them.  And looking at NVIDIA X server settings is no help either, it does not detect the second monitor and I don't see anything that sounds like it relates to my issue.   Is there a way to manually update drivers for the onboard graphics device?  Shouldn't that be taken care of when I install updates?

---

### Post by blm-ubunet on 2016-01-15
Are you absolutely sure you had one monitor plugged into the mobo jack? (multi-head).
Multi-head with X server is very hard to get the setup right..

It is much easier to use the desktop if both monitors are plugged into the same GPU..
Unless you have a top-end intel CPU with HD5300/iris-pro/iris 530, the lowly GT610 is probably faster.

The onboard graphics is intel; the FOSS driver is included with ubuntu. Usually the support get better.

IIUC Multi-head in the past required to have a custom xorg.conf file that specifies loading driver for each GPU.
And you had to use xinerama to join the mutli-head monitors into one unified display.

---

