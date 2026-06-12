---
title: "Aspire 5570Z Random Jaunty Freeze"
date: 2009-05-12
forum: Hardware
---

### Post by nasboy on 2009-05-12
I recently upgraded my Acer Aspire 5570Z laptop from 8.10 to 9.04.  Everything went smoothly, but now the laptop randomly freezes.  I don't know how to diagnose the problem. I shut off DRI and visual effects, but that has not helped.  

Has anybody else experienced similar issues?

---

### Post by metjay on 2009-05-14
I've exactly the same problem but on a **desktop** machine.
cpu: Intel Core 2 6400, 2.13GHz
board: MSI MS-7238
memory: Kingston 2GB
graphics: GeForce 7600 GS
harddisk: 2x 500GB WDC WD5000ABYS-0

I checked the system logs, but they don't show anything.
I disabled compiz, nvidia driver, virtualbox kernel module but it still freezes..

---

### Post by buntumaddy on 2009-05-15
I can confirm this behavior on 3 of my machines at home.

1. My old Inspiron 8600 with ATI Radeon 9600M and 1.6GHz Pentium M processor.

2. My new Thinkpad X60 tablet with integrated Intel graphics. Although, disabling UXA in xorg.conf seems to have helped.

3. A brand new desktop machine I put together just last week with the following configuration.
Processor: AMD X2 64 7750
Motherboard: ASUS M3N78-EM with on-board GeForce 8300 graphics chip.
RAM: 4 GB Kinston

Both my laptops used to run Hardy Heron perfectly fine and were very stable. These random lock-ups have showed up in all my machines after upgrading to Jaunty (fresh install on all three, not an upgrade).

I'm not sure if it's the graphics because new drivers apply specifically to Intel and ATI drivers. The desktop machine has no trace of Intel or ATI drivers, it's all nVidia GeForce using 180 drivers from nVidia.

And yes, disabling desktop effects does not help in this case at all.

As described earlier, only the mouse cursor moves, nothing else is responsive. Ctrl+Alt+Backspace does not work (yes, I have dontzap disabled), Ctrl+Alt+Del does not work either. Ctrl+Fx to login to a text mode shell does not work either. Only option is to hard reboot the machine.

Strange part is all processes keep running just fine though. If something was installing while it froze, it continues installing and finishes successfully. If video or audio was playing, it continues to play just fine.

---

### Post by night-wing on 2009-05-15
Same to me on 3 machines (1 netbook, 1 notebook, 1 desktop). All different graphic cards.

---

### Post by ybmatters on 2009-05-29
I'm new to ubuntu, so thought this problem was something to do with my setup, but perhaps not eh? Anyways, I seem to have solved it on my Toshiba Satellite notebook. :D

My observations:

1. For me the freeze was always during inactivity
2. I was using random screensaver mode
3. Sometimes a screensaver was frozen mid-stream. (In particular Bubble 3D, I don't think this was the only one, but it might have been)
4. I fixed my screensaver to BioF and now I've been up for over 8 days without a freeze.

---

### Post by copperhead on 2009-05-31
I also have an Aspire (a new 4530).  I've had the destop freeze twice today.  I was using firefox both times, but that's not really saying much since I'm always using firefox.

I have no idea how to diagnose this, but as you can guess, it's pretty annoying.  I'm installing ssh to see whether I can still access the box remotely when it does freeze.

EDIT: I lied when I said my mouse wasn't working. It does continue to move around the screen, but everything in the window is unresponsive.  I'm still waiting to see if I can ssh into my workstation when the desktop freezes.

MORE INFO: Just had my window manager crash hard, but it restarted and I was kicked out to the login screen.

---

### Post by ybmatters on 2009-05-31
FWIW, my experience was that during a freeze I could access a shared folder (samba) from a windows machine, but nothing I could do at the ubuntu machine would make it respond. Be interesting to see what you get with ssh.

---

### Post by copperhead on 2009-06-01
Ok... the laptop froze, but I was still able to ssh in from another computer.  I logged in and ran the top command, and saw the Xorg process was using 100% of the cpu.  I killed the process, the window manager restarted, and I got the login prompt again.

Any ideas on how to debug these sorts of things, and would love some suggestions as to where to look and what to look for.

EDIT: I disabled compiz, which I didn't really want to do, and it seems my freezing issues have gone away.  Now I'm sad. :-(

---

