---
title: "Realtek wireless adapter won't work"
date: 2012-11-05
forum: Hardware
---

### Post by Confused2570 on 2012-11-05
Hello!

I'm trying to get my Realtek adaptor to work. It was working fine until I closed my laptop lid and Ubuntu went into suspend mode. When I opened the lid and entered my password the adaptor wouldn't connect to my wifi. I've tried various other wifi's including non protected ones and WEP, WPA etc. but none of them work. Could anyone help me out? Thanks!

---

### Post by eestet75 on 2012-11-05
> **Confused2570 said:**
> Hello!

I'm trying to get my Realtek adaptor to work. It was working fine until I closed my laptop lid and Ubuntu went into suspend mode. When I opened the lid and entered my password the adaptor wouldn't connect to my wifi. I've tried various other wifi's including non protected ones and WEP, WPA etc. but none of them work. Could anyone help me out? Thanks!

Have you tried restarting?

---

### Post by Confused2570 on 2012-11-05
Yes...

---

### Post by eestet75 on 2012-11-05
> **Confused2570 said:**
> Yes...

Is your wireless interface running? Run ifconfig in terminal and post output here.
There are lots of questions, but it would be easier if you just posted the output of these commands.
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
Also this should have been posted in Networking & Wireless.

---

### Post by Confused2570 on 2012-11-05
I ran ifconfig and I get this pic

---

### Post by eestet75 on 2012-11-05
> **Confused2570 said:**
> I ran ifconfig and I get this pic

So the wireless interface is up. However, we are going to need some more information. Please post the output of the previous link that I sent you ( please turn the camera the other way)

---

### Post by Confused2570 on 2012-11-05
I've managed to get it working! I blacklisted the driver included in Ubuntu and installed the one from Realtek (rtl8192cu) and it is now working! Thanks for the tips though guys!

---

