---
title: "Nice thing Logitech Quickcam Messenger works"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by cd-r80 on 2005-09-05
Logitech Quickcam Messenger works with this HOWTO: [http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+quickcam](http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+quickcam)

And driver from here: [http://www.ketelhot.net/qcm/](http://www.ketelhot.net/qcm/)

Install as normal user. I had just activate root account (su passwd). And apt-get install xawtv. Add module quickcam to be loaded /etc/modules. I think that I got one error because off old lsusb, but install script worked anyway.

---

### Post by rwabel on 2005-09-05
there is also the spca driver. Here is the howto: [https://wiki.ubuntu.com/Spca5xx](https://wiki.ubuntu.com/Spca5xx)

The howto also mention that Spca5xx can now be found in breezy's 2.6.12!

I'm just wondering how to make it work. I've breezy and the webcam...but nothing happens

---

### Post by cd-r80 on 2005-09-07
I had to change my driver. The first one filled syslog. Anyway this works better: [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

---

