---
title: "Mouse  freeze problem ubuntu 10.10"
date: 2010-10-21
forum: Hardware
---

### Post by vrodic on 2010-10-21
Hello,

On a Fujitsu Siemens Amilo Pro V1000 FY 27 (an older laptop with mobile Pentium 4 2.2 GHZ CPU) my mouse and keyboard input freeze for about 300 miliseconds about every 10 seconds.

This is very annoying. Ubuntu 9.04 didn't have this problem. 

I've tried adding "noapic nolapic" to kernel command line but without success. 

Any suggestions?

Thanks

---

### Post by Ryan Dwyer on 2010-10-23
Same here, although it's more than just the input which is freezing. If I'm watching a video the video will freeze for a moment and the sound will hiccup. Any mouse movements will freeze until the "moment" is over and it instantly jumps to where it should be.

It happens at the same frequency you said - for about 300 milliseconds every 10 seconds.

I think it's related to kslowd000, as that process spikes during the freeze.

I'm using a Compaq Presario 2200 with integrated Intel graphics (i915 driver). Maverick, DRI2, software rendering, running metacity.

---

### Post by Ryan Dwyer on 2010-10-23
I fixed it by following these instructions:
[http://ubuntuforums.org/showpost.php?p=10000465&postcount=76](http://ubuntuforums.org/showpost.php?p=10000465&postcount=76)

It's using hardware rendering now, but it still won't run Compiz properly. More importantly, the freezing every 10 seconds has been fixed.

---

### Post by vrodic on 2010-10-25
Thank you very much. I'm now using Intel accelerated driver.

It occasionally seems this problem still happens, but the delay is much shorter, and the machine is much more usable. 

One other thing I've noticed is some gnome-terminal (and lxterminal) font corruption. Some numbers for example had a some empty bars coverning the middle of the number horizontally. 

I've since tried xorg ppa to update intel drivers and the terminal font problem is still there, though the letter U has a small empty bar near the bottom. It might be that it's just mutable across reboots. I've used a 2.6.35 based PPA kernel. I'll try with 2.6.36 based one now. 

EDIT: 2.6.36 PPA kernel + PPA xorg seems to work fine for now. Not even occasional freezes and fonts in terminal seem to be fine. 


Vedran

---

### Post by sfranzyshen on 2010-11-21
try adding "clocksource=jiffies nolapic_timers" to the kernel command line
parameter.

sudo pico /etc/default/grub

change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapci_timer clocksource=jiffies"

save changes

sudo update-grub

reboot


sfranzyshen

---

### Post by docmojo on 2011-05-08
Hi guys, I am a novice in these technical issues...

But faced this mouse freeze prob for a few days... Just struck me that, I had installed ClamAV prior to this glitch... So removed it from the system, and the problem seems to have disappeared... 

Do you'll have it installed too?

---

### Post by tysequeira on 2011-10-16
I have a Belkin Omni Cube 4-Port (which also had other mouse problems when switching machines). This was connected to a wireless mouse

Mucked around with this for an hour and then simply bypassed the Belkin (connected a separate mouse directly to the computer).

No problems

---

