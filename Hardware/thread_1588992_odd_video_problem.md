---
title: "odd video problem"
date: 2010-10-05
forum: Hardware
---

### Post by Duncan J Murray on 2010-10-05
Hi there!

I'm having a problem with a Dell Precision M2300.

When I boot up the computer from cold.  The screen remains completely blank right from boot until you hear the log-in prompt from Ubuntu.  I can log in, and it makes the usual sound, but the screen is black.

Then if I sys-request R-E-I-S-U-B to reboot it, the video mysteriously comes back, and I can boot into Ubuntu or Windows.

Then, and seemingly randomly, the screen starts to go a bit crazy - the picture will suddenly become fragmented, repeated across the screen.  Sometimes it flickers and the entire display becomes completely unreadable with noisy-random-repeating patterns going across the screen.

Any ideas??

All best,

Duncan.

---

### Post by Duncan J Murray on 2010-10-09
Seems to have settled down a bit now.

I reanabled the Nvidia proprietary driver, and switched off compiz.  It seems to be working much better now, although if you leave it on for a while, the same problem seems to reoccur.

What is bizarre is that when the problem happens, it affects the BIOS screen on boot-up, implying that whatever is going wrong, is happening with the graphics card.

Could this be caused by a faulty graphics driver setting the graphics card in such a way that it retains these problems even when the laptop is off?

I have installed Lm monitors to keep an eye on the temperature of the gpu and cpu.  I played alien arena on high settings for about 15 minutes, getting the gpu temp up to 80 deg c, with no problems.

Anyone got any ideas?

It's my fiance's laptop, and she's starting to think linux may be to blame!  She's thinking of installing Win XP back on it.  I'm not sure whether this would solve the problem or not.

Duncan.

---

### Post by Duncan J Murray on 2010-10-09
Another update:

Just attempted to switch on the laptop - this time the screen completely black.  I could hear the harddrive being accessed in the usual way as it boots up, but this time, using sysreq_rusieb simply rebooted the computer, but without recovering the display.  I was even able to hold down shift, and select another kernel (of course without any display) and get it to boot up that, but to no avail.  There were no system sounds or samples played this time.

It was only after powering off the computer and then booting up which has allowed the display to work again.

Any ideas anyone?  Any log files which might be useful here?

Thanks,

Duncan.

---

### Post by Duncan J Murray on 2010-10-12
Thought I'd post this in case anyone else has similar problems, but it's starting to look like a gpu problem.  Dell have extended the warranty by 12 months with regards to this specific problem.

---

