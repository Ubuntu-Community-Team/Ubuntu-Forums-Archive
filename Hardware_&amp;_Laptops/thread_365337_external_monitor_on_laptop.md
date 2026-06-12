---
title: "external monitor on laptop"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by ktodac3298 on 2007-02-19
i have a laptop with windows and linux on it. the screen is broken well its cracked. so i use an external lcd monitor. for windows i just go into display settings and tell it to do the clone thing . however i dont know how to do this in linux. when i plug in the monitor, all that shows up are lines, what setting and how do i change this in ubuntu??
plaese help

---

### Post by tgalati4 on 2007-02-20
Dear ktodac

LCD screens look best at their native resolution.  You need to tell the xserver to output this exact resolution.  If you have access to an old CRT monitor, I would hook that up to see what you are doing.

Linux requires a little effort to get dual screen, but it does work.  In your case you really only need the external screen so you would set active display "1" and set inactive display "0".  Again it requires tweaking the xserver settings in the xorg.conf file (try locate xorg.conf).  But any of this editing requires a CRT that you can see.

You can log in through the net and change these settings, but you have to activate SSH first, and you need to see what you are doing anyway.

Getting proper video settings can be a pain, but once it works, it works well and you won't have to mess with it again.

Sadly this is one area where Windows has an advantage.

Good luck,

Terry

---

