---
title: "Touchpad too slow"
date: 2005-03-15
forum: Hardware &amp; Laptops
---

### Post by axmanak on 2005-03-15
I recently updated my Dell Latitude D505 form Warty to Hoary. That was mainly painless, but my touchpad stopped working as before. It reacts much slower now and I can't tap anymore.

If I boot my old kernel (2.6.7-something compared to the actual 2.6.11-sth.) the touchpad works as expected, but not with the actual kernel.

Any idea how I can fix this?

---

### Post by smtanner on 2005-03-16
Is that a synaptics touchpad?  My synaptics touchpad is working fine with 2.6.10 kernel on Hoary.  Is there some reason you need to use 2.6.11?

---

### Post by axmanak on 2005-03-16
I tried various kernels, mostly from the ubuntu-servers. I compiled 2.6.11. myself just for the fun of it.

I am not sure if I have a Synaptics Touchpad. It worked out of the box, so I didn't care until now. (I looked at my dmesg output and my loaded modules. Found nothing like synaptics)

---

### Post by smtanner on 2005-03-17
The touchpad in your laptop is an ALPS.  I did some quick searching and it looks like there is not support for this in Hoary right now.

Maybe this link will help you:

[http://www.gossamer-threads.com/lists/linux/kernel/518668](http://www.gossamer-threads.com/lists/linux/kernel/518668)

[http://marc.free.net.ph/message/20050304.221523.18786251.en.html](http://marc.free.net.ph/message/20050304.221523.18786251.en.html)

[http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

---

