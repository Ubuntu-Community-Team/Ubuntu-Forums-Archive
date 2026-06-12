---
title: "nvidia driver problem"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by tommy_haaland on 2005-06-02
I have a Gainward geforce fx 5200 card whose driver doesn't seem to work. 

First I did this:

1. sudo apt-get install nvidia-glx
2. sudo nvidia-glx-config enable


Then the install procedure automatically changed my xorg.conf; the only thing it did was the change Driver from "nv" to "nvidia"
Then I rebooted, and gnome wouldn't start. When I change xorg.conf Driver back to "nv" there is no problem...

I looked at Xorg.0.log

Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

Can anyone please help?  :)

---

### Post by alastair on 2005-06-02
I don't think those are "errors" (maybe). There is pobably something else.

Post a more complete /var/log/Xorg.0.log.

Also - no need to reboot if you change graphics drivers.

Just stop/start X e.g.

CTRL+ALT+BACKSPACE at the login/GDM screen
or
/etc/init.d/gdm restart  (from a terminal)

---

### Post by shelbydz on 2005-06-27
did you figure this out?? I'm having the exact same problem. This was right after I installed Kino and all it's componets. I restarted X, then it wouldn't get past the gnome startup screen (where it's loading all the stuff).

. . .shawn

---

