---
title: "Can't get past 640x480"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by mzellers on 2007-04-20
Hi,

I'm trying out Feisty Fawn on a Toshiba Portege 7200 series laptop, and I can't get the screen to any size other than 640x480.  I'm sure I was at at least 800x600 if not 1024x768 with Red Hat (which I just wiped).

Is the display card for this machine not supported.  The Device Manager reports it as a Trident Cyber 9540.

If I can't get more screen real estate, its back to Fedora I'm afraid.

---

### Post by NotoriousTF on 2007-04-20
Hey
I'm also having a similar problem. I've just upgraded from 6.10 via the update manager, and my resolution can only be set to either 640x480 or 600x800. Everything just looks so wrong!
I must add that my graphics card isn't currently supported, but from using previous versions of Ubuntu, I've never been able to use my graphics card and changing resolution has never been a problem.

---

### Post by NotoriousTF on 2007-04-20
Hey mzellers,
Have a look at this thread [http://ubuntuforums.org/showthread.php?t=411489](http://ubuntuforums.org/showthread.php?t=411489) by anujseth.
I eventually got my monitor running using the 1024x768 resolution (though my refresh rate is marked as 0Hz??). I tried out what the original poster suggested, but this didn't work for me, as I didn't know all the specs for my laptops monitor.  I noticed another user, boccaccio posted suggesting that the resolution settings could be altered using the command line:

sudo dpkg-rreconfigure xserver-xorg

This worked perfectly for me! Make sure to restart your laptop when you've finished, and you should notice the changes on the log in screen. Then log in and change the settings in the 'Screen Resolution' menu.
Hope their advice works out.

---

