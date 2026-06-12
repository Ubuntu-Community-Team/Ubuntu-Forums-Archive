---
title: "USB hard drive won't autodetect; already reinstalled hotplug using synaptic"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by jang on 2005-08-17
Any ideas?  When I connect a usb hard drive, nothing happens.  I remember when I first connected it, it worked, now, it doesn't

---

### Post by heimo on 2005-08-17
I recall reading others having this same problem, and it may be related to latest kernel updates. On terminal, run:

 ```
sudo tail -f /var/log/messages
``` 
*) I'm not sure if sudo is neccessary.

And while wathing that log, insert the USB stick. Any messages?

You could try to install older kernel, but if I recall correctly, latest had security patches. Not sure about that either. Or, you could try to use even newer kernel, great howto by tseliot is here (it's good for advanced users too, not just newbies):
[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

---

### Post by jang on 2005-08-17
yes, a few lines, then finally "sd_mod: loaded sucessfully" but nothing else on desktop

---

