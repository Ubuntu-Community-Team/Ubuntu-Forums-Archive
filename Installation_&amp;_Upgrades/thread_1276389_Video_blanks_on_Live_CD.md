---
title: "Video blanks on Live CD"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by scrabblegod on 2009-09-27
When I try to run the live cd, the screen blanks.
If I do a regular Live Cd run, after the Ubuntu Splash screen and scroll bars stops, my screen blanks and says no signal.
If I run the Live cd with the safe graphics option, after the Splash screen, i just get a blank screen, but it does not give the no signal message.

I have a DELL XPS 410 with an ATI X1900 GT hooked to a Proscan 26" lcd through HDMI

Any thoughts,
Thanks,
Gene

---

### Post by rreese6 on 2009-09-27
most likely you will have to configure the HD output once you get it set up, use a standard VGA monitor to do the setup.

---

### Post by scrabblegod on 2009-09-27
> **rreese6 said:**
> most likely you will have to configure the HD output once you get it set up, use a standard VGA monitor to do the setup.
Yea, but my video card has no VGA output. 
If I stick an old VGA card in and do a full install, what would be the steps to go back to the HDMI card?

---

### Post by rreese6 on 2009-09-27
ok if you use a vga card to do the OS installation. 
Then you will want to download Catalyst drivers (8.29.6)
at this point I would suggest rebooting into recovery mode to kill the xserver.
drop to the root prompt from the recovery menu

You need to copy your old xorg.conf ```
cd /etc/X11
cp xorg.conf xorg.conf.vga 
```

Install the ATI Drivers (read their install directions)
not sure if we should try to change out he cards at this point and try to reboot
to the recovery console or not. we could try it and if it doesn't work, swap the vga back in.
then run
```
 ./aticonfig --initial=/etc/X11/xorg.conf
```

Also, you'll want to un-comment the "dri" section in your xorg.conf to harness hardware rendering.
```
 sudo nano xorg.conf
```
remove the "#" in front of the "dri" section
Hit CTRL X to exit, save and enter.

I think that just might work...it's been a long day  See you later

---

