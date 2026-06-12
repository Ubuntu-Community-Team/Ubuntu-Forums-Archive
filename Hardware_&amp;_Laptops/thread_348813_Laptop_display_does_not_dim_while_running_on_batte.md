---
title: "Laptop display does not dim while running on battery"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by rmx.dave on 2007-01-29
Hi everyone,

My Sony Vaio VGN-FJ170 display does not dim when the power is unplugged - or at all for that matter. I adjusted the properties in the gnome power settings, but nothing happens, the display is at 100%. I would like to get it down to like 70% while on battery to save power - right now the thing lasts just about 2 hours with the CPU underclocked to 800 mhz. 

I originally had Dapper installed but I recently upgraded to Edgy. The brightness settings worked in Dapper. 

If anyone knows what software I'm missing or what I need to do, any help is greatly appreciated. 

Thanks,
rmx.dave

---

### Post by CSMatt on 2007-01-30
I have the same problem with my Sony VAIO VGN-FE660G.

---

### Post by K.Mandla on 2007-01-30
You might check your BIOS settings for power management. On my Dell laptops, the BIOS has an option to dim the screen on battery, and that might supercede any software settings. Just an idea, I guess. ... :-k

---

### Post by rmx.dave on 2007-01-30
I just looked in the BIOS, there was nothing there regarding power save settings or anything. I didn't think there was - since Dapper was able to change the brightness without making any BIOS adjustments.

---

### Post by CSMatt on 2007-01-30
^ What he said.

---

### Post by kristalsoldier on 2007-03-03
I am running a Sony Vaio VGN-FE28B and Edgy...and fiddling with the power mgmt to dim the screen (I've set it to 50% on battery) does not seem to work!

---

### Post by kilou on 2007-04-29
You might want to try this:

sudo mv /bin/sh /bin/sh.bak
sudo ln -s /bin/bash /bin/sh

details here: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/65028](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/65028)

This seems to work for Vaio laptops but I have an MSI S260 and it doesn't work for me. I can adjust brightness with Function+F4/F5 but when I switch laptop to battery the screen dim only by 3 notches. However in gnome configuration editor under apps/gnome-power-managment, battery brightness is set at 1 and AC brightness is set at 100... If anyone know how to solve this please let me know. Thanks

---

### Post by rmx.dave on 2007-04-29
Amazing. I found a temporary fix using the brightness app from Linux Mint, but this is finally working the way i want it to! Thanks a ton!

---

### Post by CSMatt on 2007-04-29
Too bad this didn't come before I ditched the VAIO for unrelated reasons, but thanks anyway.

---

### Post by Mike Carter on 2007-09-06
Thankyou very much for the solution, its working perfectly now :)

---

