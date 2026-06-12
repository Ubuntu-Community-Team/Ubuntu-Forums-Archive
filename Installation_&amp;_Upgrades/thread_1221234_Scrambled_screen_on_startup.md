---
title: "Scrambled screen on startup"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by daveldhu on 2009-07-23
Hi everyone,

This issue started happened randomly one day. Just installed Jaunty and got it all up and running ok, so I installed Catalyst Control Center and did all the updates the update manager wanted me to do, and then restarted when told to. Problem is when it boots back up, grub loads fine and everything, it shows the splash screen with the progress bar on it, then when it goes to show the desktop, it goes all scrambled. As far as I can tell it boots normally, the display is just scrambled.

So I looked around, someone somewhere suggested booting with no splash screen, still no luck.

Wierd thing is that this happened when I tried to install Mythbuntu 9.04 too, except it never let me boot normally, scrambled every time.

The computer is running a ATI X800. This also happened on another computer too with an X1650 PRO, and the best I could manage there was to boot in low graphics mode, but now I'm forced to work in 800X600 (N)!

I'm lost, so any suggestions would be appreciated

---

### Post by kdetech on 2009-07-23
Install startupmanager then run it and configure boot resolution

---

### Post by Mark Phelps on 2009-07-23
> **daveldhu said:**
> ...so I installed Catalyst Control Center...
CCC does not work with your card in Ubuntu 9.04. Nor does it work with a x1650. You will need to remove the restricted driver and use the open source driver instead.
> Wierd thing is that this happened when I tried to install Mythbuntu 9.04 too, except it never let me boot normally, scrambled every time.
Not weird at all -- same 9.04 problem.

> This also happened on another computer too with an X1650 PRO, and the best I could manage there was to boot in low graphics mode, but now I'm forced to work in 800X600 (N)!
Same no-restricted-drivers-from-ATI-for-9.04 problem.

---

### Post by daveldhu on 2009-07-23
Thanks for the replies everyone.

So I did a fresh install on both computers without CCC and everything works. Only problem now is that when I hook up the X800 to my tv with an HDMI cable, I get a black screen. When I hook it up to a monitor with DVI I get a scrambled screen still. Is there a way I can get the dual display (DVI + VGA) working w/o CCC, because without dual mode I can't boot and adjust settings to make the HDMI output work.

---

### Post by daveldhu on 2009-07-24
Ok so I got the dual display thing to work by adding a virtual display to my xorg.conf file. Now the problem is it will show both screen if I hook bout output to monitors, but when I plug it into my tv with a DVI-HDMI cable, all I get it a black screen. 

I assume this has something to do with an incompatible resolution or refresh rate, but in the display menu it only gives me a few options for each (even though there's a lot more options for "modes" in my xorg.conf file). Any idea how to do this? I don't have the file right now, but I'll try to post my xorg configuration later today.

Thank you!

---

