---
title: "screen goes black repeatedly in gutsy gibbon: bcm43xx or fglrx to blame?"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by cuernitech on 2008-01-11
I am totally new to ubuntu -- its been three days since I installed Gutsy Gibbon and ive spent every waking hour trying to fix the bugs inherent in my gateway laptop 7246GX (relevant hardware: AMD Athlon64 3700+, ATI Raedon 9600 M10, Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03))
... I had some issues with my ATI card (who doesn't) after I installed advanced desktop effects (compiz-config, xgl, gnome-compiz-manager) and the screen goes black while watching an .avi in movie player. I recovered this error message in the log:

Jan 11 00:15:11 miramon-laptop kernel: [ 3628.681204] [fglrx:firegl_lock] *ERROR* Process 5177 is using illegal context 0x00000004

so I got turned off all the desktop effects and removed:

compizconfig-settings-manager
gnome-compiz-manager
xserver-xgl

I though this would solve the screen-going-black problem, however the laptop continues to freeze...

(keep in mind that my laptop screen goes black and the CPU fan blows like a tornado -- all I can do is turn off and turn back on -- can't reboot -- whole thing is locked up on every one of these 'freezes' I'm talking about)

so, after all the compiz and xgl junk is removed completely certain other tasks will trigger the freeze:

(1) downloading a torrent using bittorent, which causes the following errors 

syslog:

Jan 11 18:15:02 miramon-laptop kernel: [ 3715.201638] bcm43xx: MAC suspend failed    <---------------This one occurs every ten minutes anyway. ------>
Jan 11 18:17:04 miramon-laptop /USR/SBIN/CRON[6367]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

kern.log
Jan 11 18:15:02 miramon-laptop kernel: [ 3715.201638] bcm43xx: MAC suspend failed

The 18:17:04 is the LAST syslog entry before the computer freezes... any idea what that means?

(2) watching a movie (STILL) even though I removed all the GL stuff.
this is the last entry in the syslog and kern.log:

Jan 11 19:23:32 miramon-laptop kernel: [ 1650.483980] bcm43xx: MAC suspend failed

(3) attempting to browse home network (samba installed -- other comp is running XP) and browsing internet to post this message  :) 

Jan 11 19:38:21 miramon-laptop kernel: [  163.418938] ADDRCONF(NETDEV_UP): eth0: link is not ready

SO... In my limited wisdom I believe it has something to do with fglrx or bcm43xx (or both)... any ideas?

---

### Post by Yellow Pasque on 2008-01-11
Why not try running without fglrx? The open-source radeon driver should work best for a 9600.

---

### Post by cuernitech on 2008-01-11
Thanks for your reply, Temüjin. 

In my limited wisdom I have completely removed fglrx using synaptic package manager... now ubuntu can't boot up.

it gets stuck on trying to load - the last thing it says is: 

Running local boot scripts (etc/rc.local)     [OK]
{blinking cursor here}

what did I do?!?!?

---

### Post by strabes on 2008-01-11
After you receive that message, can you get to a terminal by hitting ctrl+alt+f1? If so, log in and run these commands:```
sudo aptitude update
sudo aptitude install xorg-driver-fglrx
sudo aticonfig --initial -f
sudo nano /etc/modprobe.d/blacklist
```

Then at the end of that file, add "blacklist fglrx" and save (ctrl+o) and quit (ctrl+x). Then reboot your computer. This will force your computer to use mesa.

---

### Post by Yellow Pasque on 2008-01-11
> **strabes said:**
> After you receive that message, can you get to a terminal by hitting ctrl+alt+f1? If so, log in and run these commands:```
sudo aptitude update
sudo aptitude install xorg-driver-fglrx
sudo aticonfig --initial -f
sudo nano /etc/modprobe.d/blacklist
```

Then at the end of that file, add "blacklist fglrx" and save (ctrl+o) and quit (ctrl+x). Then reboot your computer. This will force your computer to use mesa.

No, I wanted him to run with the "radeon" driver, not fglrx, so we could try and isolate the problem.
cuernitech, when the boot process gets hung up at that screen, press Ctrl+Alt+F1. Login to the terminal and run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the "radeon" driver.

---

### Post by Yellow Pasque on 2008-01-12
Now that I think about it, it also sounds like it could be a CPU overheating problem. Do you have lm-sensors installed? Are you monitoring CPU temps?

---

### Post by cuernitech on 2008-01-12
strabes: thx for post - you got me up and running again  :)

Temüjin: I ran ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and it gave me:
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080112011219

```

after a few screen flickers.

I am monitoring the CPU temp -- its in the 34C-38C range but at time it gets as high as 45C!

I think that's the problem. It would make sense that when I start to do anything graphics-intensive or excessive HD activity it would super-heat. Case closed.

This sucker is still under warranty (phew).

Thanks for your help!

---

### Post by Yellow Pasque on 2008-01-12
So it's under 40C at idle and 45C at load? Those temps are perfectly fine. Generally, as long as your CPU is below 60C, you're good.

If the problem keeps occurring, I would still try removing fglrx and running the radeon driver, to see if fglrx is to blame.

---

### Post by cuernitech on 2008-01-12
Ok... I have disabled the fglrx driver (screenshot-fglrx) and am using the Radeon driver (see screenshot-driver - just to make sure I have it set up right)

While watching a movie in move player (after about 4.5 minutes), temp peaked at 74C and computer screen went black, fan spinning. When I rebooted, a strange error message popped up (see screenshot-gnome).

I included the Xorg.0.log as a text file just in case this would help shed some light on what the video drivers are doing.

I guess it isn't the fglrx driver... very curious...

---

