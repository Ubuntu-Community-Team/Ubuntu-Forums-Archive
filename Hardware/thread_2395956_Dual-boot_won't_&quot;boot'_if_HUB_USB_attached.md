---
title: "Dual-boot won't &quot;boot' if HUB USB attached"
date: 2018-07-09
forum: Hardware
---

### Post by liris31 on 2018-07-09
I have a dell XPS 15, with a dual-boot (windows 10 and ubuntu 16.04 on it).
I just got a new 3-USB hub ([https://www.reichelt.com/fr/fr/?ARTICLE=160709&PROVID=2788&gclid=CjwKCAjwj4zaBRABEiwA0xwsP7Em9502cv9b5RU0T7JJjRJh_6dlJwJm_RG6KeAPuvQ9prn3rhNafxoCZskQAvD_BwE](https://www.reichelt.com/fr/fr/?ARTICLE=160709&PROVID=2788&gclid=CjwKCAjwj4zaBRABEiwA0xwsP7Em9502cv9b5RU0T7JJjRJh_6dlJwJm_RG6KeAPuvQ9prn3rhNafxoCZskQAvD_BwE)) with also a port Gigabit.

When I start the computer with the HUB attached, it won't boot and it stays stuck on the Dell logo, before grub show my boot options. To be more precise, even if I remove the USB hub when it's stuck on the dell logo, nothing happen and I have to reboot. If I start my computer without the USB hub attached, everything is going fine.

I just had a look on [https://ubuntuforums.org/showthread.php?t=2304842](https://ubuntuforums.org/showthread.php?t=2304842) which seems pretty close to my issue. However, because I don't even reach the point where I can choose betwwen ubuntu and windows, I don't really know where to start on that one.


I would appreciate any hint about that !

EDIT : solved it by updating BIOS from 1.6 to 1.7 using the DELL support website.

---

### Post by Autodave on 2018-07-09
Just a thought: you don't have the BIOS set to boot to USB before the HD(s) , do you?

---

