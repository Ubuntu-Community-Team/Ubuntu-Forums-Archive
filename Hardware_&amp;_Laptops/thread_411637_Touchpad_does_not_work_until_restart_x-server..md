---
title: "Touchpad does not work until restart x-server."
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by JSHN on 2007-04-17
I have read in this forum about people having trouble with the touchpads in x-server, that
they need to restart x-server to get it to work. I haven't seen any solution and I'm myself
struggling with this problem. Also this seams to be a Sony Vaio problem. (Probably similar touchpads.) =/

I found some interesting things when trying to debug why it does not work, now
I need your help to solve this =))

One thing I noticed is that all the drivers are loaded correctly but it does not wake up
the touchpad at first. Many people notice that the touchpad works after restarting x-server
but why this is working is that when you move around on the touchpad for a few seconds it
wakes up and then starting to work. And when you restart x-server after this, it talks the touchpad and
the settings are applied.

You can get the touchpad working without restarting x-server and that is if you move around on the touchpad
on the booting progress when loading x-server, then you will see that the device has been waken up and
working on boot. But I want to start my lappo, walk away and when I get back it should work right away.

Is there any way to talk to the touchpad to try to wake it up at boot by itself???

Please replay if you have any other interesting info about this!
I will try anything! :D

---

### Post by JSHN on 2007-04-17
Also when laptop is waking up from hibernation the touchpad-settings is lost.

---

### Post by JSHN on 2007-04-17
I checked the synaptics driver with: "sudo apt-cache show xserver-xorg-input-synaptics"
And found this line:
"Conflicts: xfree86-driver-synaptics, xorg-driver-synaptics"

I checked a standard installation and this conflict is there also, probably nothing
but might be good to know.

---

