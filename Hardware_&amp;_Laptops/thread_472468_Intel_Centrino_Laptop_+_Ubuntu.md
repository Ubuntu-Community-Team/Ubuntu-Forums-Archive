---
title: "Intel Centrino Laptop + Ubuntu"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by masterperas on 2007-06-13
I installed feisty fawn on my intel centrino laptop, had some trouble getting the wireless to work but i finally managed it

every thing works great till i decide to put wep encription on my router. i tried using a 64 bit and a 128 bit key but even when i turn it on i lose my wireless connection. i'm trying to use the gnome network manager.

any help?

if u need more info please let me know

---

### Post by jotagab on 2007-06-13
Hi!
Which WiFi chipset do you have? Because even in a centrino platform you can have some other than an Intel WiFi chipset (i2200, i3945, etc.).
I also have a centrino laptop with an Intel 2200 WiFi chipset and I had some problems using Gnome's Network Manager with WPA set in the router (by the way, you should use WPA instead of WEP; WEP is too insecure). I ended up using some other application which I don't remember the name (I'll post it later in the day).

---

### Post by jotagab on 2007-06-13
Hey again!
Like I mentioned before, I also have a centrino. I managed to have the wireless working without any encryption using Gnome's Network Manager in Feisty, but the moment I set up WPA in my Linksys router I couldn't use it anymore. My solution was to uninstall Network Manager and install Wicd (available from Synaptic) instead.
However since I'm 99% of the time connected by ethernet this was basically a test, so I don't have much to say regarding stability...
Cheers, hope this helps!

---

### Post by masterperas on 2007-06-14
thx for the replied bud

ill have a look into what u just said

---

