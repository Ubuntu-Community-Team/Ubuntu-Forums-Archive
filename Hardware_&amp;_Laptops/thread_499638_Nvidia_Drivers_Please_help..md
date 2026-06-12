---
title: "Nvidia Drivers Please help."
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by goo3r on 2007-07-12
Hi, I am very new to linux, but not new to computers in the least. I am trying to install beryl with ubuntu fiesty and everytime I upgrade my nvidia drivers and enable acceleration, when I restart I get a black screen and my laptop LCD doesn't work, but it works with the VGA port in the back.

I have an dell inspiron 8100 with a geforce4go card in it. I have been fumbling with this for quite some time and can't seem to find an answer that works. Please help!

---

### Post by bdtgp on 2007-07-12
The GeForce 4 series typically runs on either the nvidia-glx or nvidia-glx-legacy drivers.  If you're trying to upgrade to the nvidia-glx-new it probably won't work as well.  Go to the synaptic package manager (System>Administration>Synaptic Package Manager) and try to remove the newer drivers and opt for the older ones.

---

### Post by goo3r on 2007-07-13
They are set to the nvidia-glx drivers, but when I enable acceleration, I can only get video through the VGA port in the back and not onto my laptop's lcd. I saw a page that talked about this problem and editing the xorg.conf file, but I guess I am not that good yet to figure it out. Thanks for the help though.

---

### Post by goo3r on 2007-07-13
I figured it out. It turns out you have to edit the xorg.conf file. Then add Option "UseDisplayDevice" "DPF" after Depthdefault in the Section "Screen" I hope this helps others.

---

