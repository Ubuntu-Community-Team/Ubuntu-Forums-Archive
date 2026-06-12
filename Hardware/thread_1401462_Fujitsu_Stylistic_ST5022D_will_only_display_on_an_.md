---
title: "Fujitsu Stylistic ST5022D will only display on an external monitor"
date: 2010-02-08
forum: Hardware
---

### Post by Charleh on 2010-02-08
I just installed 9.10 on my Fujitsu Stylistic ST5022D tablet pc, the installation went fine. I restarted it, ready for use, the GRUB menu appeared and I chose the first option (Ubuntu 9.10). The screen then went blank but the HDD indicator still flashed.

I wired it up to an external VGA monitor and it loaded the BIOS splash screen and the GRUB menu on my tablet and loaded Ubuntu on the monitor.

I logged into Ubuntu, opened "Display" and it shows my external 19" monitor as the only display.

It uses Intel 855 graphics and installed fine for the gentleman [here]("http://www.alfonsomartone.itb.it/zswdjp.html").

---

### Post by Charleh on 2010-02-09
Will attempt to install 8.10 instead

---

### Post by naviathan on 2010-10-06
So is this as far as you've gone with this?  I'm looking at putting either 10.04 or 10.10 on mine, but I'm curious what caused it to go to the external only?

---

### Post by naviathan on 2010-10-09
Ok I tried kubuntu 10.10 and it worked (except for the buttons) but it was horrendously slow.  ubuntu 10.04 gets to the splash screen then goes black and all hard drive activity ends.  Think I should try either ubuntu 10.10 or xubuntu 10.10 to see if that alleviates the slow problem and still allows it to boot.

---

### Post by gordintoronto on 2010-10-09
What are the hardware specs? Memory?

---

### Post by naviathan on 2010-10-10
Celeron 1.1GHz, 1G of ram, Intel i855 integrated video and Wacom digitizer.  It's mediocre performance wise, but with a decent Linux install I think it's could be worthwhile for photo editing.

A little update, Ubuntu 10.10 loaded quite well, I'm just having issues with the screen rotation.  The fjbtns program initially only rotates the wacom, it seem xrandr is disabled somehow.  I uploaded an xorg.conf I found and it rotated the screen, but didn't change the resolutions around so I ended up with only half the screen in the elongated rotations.  I made some changes to the xorg.conf that I thought might help, but unfortunately I was wrong, it only made the machine stop loading on boot before the splash.  So now I'm thinking about switching back to Fedora Design which rotated the screen well, but not the wacom.  If I can get fjbtns in Fedora it should work.

---

