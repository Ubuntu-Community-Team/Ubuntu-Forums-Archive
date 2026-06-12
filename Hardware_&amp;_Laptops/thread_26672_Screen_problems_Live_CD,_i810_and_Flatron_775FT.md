---
title: "Screen problems: Live CD, i810 and Flatron 775FT"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by Miguel on 2005-04-13
Hello everybody,

I am currently running Warty on my laptop (Dell Inspiron 8600c) and SuSE 8.2 on a dektop at university. The thing is, I have both the live CD and the intall CD of Hoary and I plan to install it on both computers (I was going Debian Sarge on the desktop, but it hasn't gone gold).

Both machines are important for my job, so I have tried first the live CD. On the laptop it runs flawless. Impressive. I *need* to see it off the HD. It also runs great on my father's PC and on a friend's brand new PC (had to show them linux). But on my university desktop... no joy. I suffer from display problems

That PC is a P4 at 2.80 GHz, 512Mb RAM, an integrated i810 graphics card and a LG Flatron 775FT (17 inches, 1280@60Hz). The installer runs fine, but then GNOME loads at 640*480. There are more resolutions available. After that, I turn off Gnome and switch to the tty1. I edit the Xorg config file (using sudo, BTW), kill the X and then restart GNOME. While I can now select the desired resolution (1024@85Hz), I see ghost images, missing icons, parts of windows that I closed a few moments ago...

I'd be glad to know if anyone has seen (and hopefully solved) this problem. Also, Is this a hardware issue? A X.org issue that wouldn't happen on Warty (even though Hoary's hardware detection seems top notch)? Or a live CD issue?

If anyone is interested, I can post both SuSE 8.2 XF86Config and Xorg config (don't recall the exact name) files of that PC. 

Thanks in advance

PS: No matter what happens to the desktop, on monday this laptop will be running Hoary.

---

### Post by nad on 2005-04-13
Warty uses the XFree86 X server. Hoary, Xorg. There are dozens of posts here regarding issues with the Xorg X server.

Where does SuSE come into this?

Dan M

---

### Post by Miguel on 2005-04-14
Suse enters in the equation in:

"My current XF86 setup works, but Xorg (at least in the Hoary live CD implementation) doesn't".

Thanks for the reply.

---

