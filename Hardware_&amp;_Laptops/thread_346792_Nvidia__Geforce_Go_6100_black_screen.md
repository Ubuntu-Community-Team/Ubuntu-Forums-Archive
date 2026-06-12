---
title: "Nvidia  Geforce Go 6100 black screen"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by mangaeva on 2007-01-26
I have an MSI Megabook M670 laptop with AMD Sempron 1.8 Ghz processor, 1GB RAM, Nvidia Geforce Go 6100 and wide screen.  I was really happy that i could start to use Linux. Im really new for everything and first i thought that the problem is in me when i tried to install the nvidia driver. but after i found automatix i realized that its not cause me that i get a black screen when i could sign in. I hear the drums and such just cant see anything. I tried out things i found on the net but non of them seemed to work.

I attached my xorg.conf (hope you can see it im kinda new for this forum too)

Every idea is Welcome, i really dont know why i cant fix it, tho cause im really new to this all, im not really knowing what im doing, but im really sad about it that i couldnt make it alone.

Hope one of you guys can help me. I fee like a noob, but im reading about linux in the past 2 days. So i hope that i will get better.

Thanks for every help. Hope that finnaly i will be able to use the nvidia and the wide screen resolution.

---

### Post by renzokuken on 2007-01-26
If you have the nvidia driver installed, then go down to the Section "Device" in your xorg.conf and change the line

Driver  "vesa"

to the following

Driver  "nvidia"

save it and reboot and see what happens

---

### Post by mangaeva on 2007-01-26
No the driver is uninstalled. When i install the driver and look into my xorg.conf it has the Nvidia...uhh maybe i should copy the xorg while the driver is installed..uhh im stupid...just a sec

---

