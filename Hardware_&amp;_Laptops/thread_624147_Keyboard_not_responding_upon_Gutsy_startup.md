---
title: "Keyboard not responding upon Gutsy startup"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by checho4 on 2007-11-26
My keyboard on my Inspiron 1501 is no longer working in Kubuntu Gutsy 64bit. Everything seems to load up fine. At the login screen, I can press alt+ctrl+Fx to open up a command prompt and run tasks there. However, as soon as I log into KDE, my keyboard stops working.

Also, using the on-screen keyboard (and clicking on each key with my mouse), I can execute "ping google.com" successfully, showing me that I AM connected to the internet. However, when I try to log onto the internet, no network is found.

Also, when I try to shutdown, I get an error that says something along the lines of:
Unmounting local filesystems
"/" device is busy

The shutdown process just hangs there.


Any help is GREATLY appreciated!!! Thank you!

---

### Post by dabl on 2007-11-26
Maybe this will help with the shutdown thing:

[http://kubuntuforums.net/forums/index.php?topic=3087145.0](http://kubuntuforums.net/forums/index.php?topic=3087145.0)


On the keyboard, try going into BIOS and setting the USB to "legacy".

:)

---

### Post by checho4 on 2007-11-26
I think I found the problem, though I don't know WHY it's the problem.  I set kNetworkManager to NOT startup automatically, and then I restarted [using the power button].

Upon logging in, everything worked.  Then, I started kNetworkManager to connect to the internet.  That worked.  I rebooted [via KMenu => Restart] and everything went smoothly.  Could it be a bug in kNetworkManager?

---

### Post by dabl on 2007-11-27
> **checho4 said:**
> 

Could it be a bug in kNetworkManager?



YES.  I don't use wireless, but the reported problems with KNetworkManager are many and varied. :)

---

