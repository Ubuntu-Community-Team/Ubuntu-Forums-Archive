---
title: "Logitech Mouse configure"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by alatham on 2007-05-22
I've read all the other posts on configuring Logitech mice, but nothing even touched on my current problem.

I'm running Ubuntu Studio with a Cordless Logitech LX7 mouse.  When I run Jack at a low latency (which I should be able to do), I get an xrun every 30 seconds.  I've finally narrowed it down to my mouse.  I can unplug it and it works perfectly, but when the mouse if plugged in, I get the xruns.  I've also tried switching USB ports around, but that didn't help (which is what I expected).  I'm assuming that it's the mouse's battery charge detection that's causing problems.

When I open up the Device Manager, I can see two things that interest me:

1)  Ubuntu thinks I have an MX1000 mouse.  This doesn't really bother me as all the buttons work fine though (at least the buttons I actually use).  I'm wondering if there is a more specific driver I can use.  This is not as important as my other issue though:

2)  In the advanced options for my driver, it looks like I'm supposed to be able to change values like "battery.present"  It's listed as a bool, and I can double click the value and try to change it, but as soon as I hit enter it just reverts to the original value.  Does anyone know if I can change these values somewhere?  And even assuming I can, does anyone think this will shut off the battery detection for the mouse?

Thanks, great distro.  I just have one more hiccup to work out.

---

### Post by nioakeim on 2007-05-23
Would you like to try to plug in the mouse to a PS/2 port and see what happens?

---

### Post by alatham on 2007-05-23
I don't have a PS/2 mouse handy.  But I have plugged my girlfriend's Kensington USB Wireless Mouse in and it worked perfectly with no xruns.

It's been suggested I use the same mouse, but try to get it running with a generic 2-button + mousewheel driver.  I don't ever use any of the other buttons, so this doesn't bother me.

I guess it might be a bug in the MX1000 mouse driver.  Does anyone know how to contact the people that wrote that driver?  It wasn't Logitech as far as I know.

Also, can you tell me how to manually install a generic driver for the mouse?

---

