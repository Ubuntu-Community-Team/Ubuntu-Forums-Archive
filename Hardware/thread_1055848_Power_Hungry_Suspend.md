---
title: "Power Hungry Suspend?"
date: 2009-01-31
forum: Hardware
---

### Post by Naughty 240 on 2009-01-31
I have an IBM Thinkpad R51, running Ubuntu 8.04 with all updates, and have made a few tweaks to reduce power usage, and have got it down to 11-12w during normal use with WiFi on, could be less, but POWERtop doesnt work for me. Anyways, the suspend function works fine, as in when i close the lid it enters suspend mode. Bu heres where the problem is, in Windows the laptop uses about 5-10% of power ever 2 hours while in suspend, and goes cold as if its off. In ubuntu it uses about 20% every hour and the laptop is still warm as if its running, but the suspend light is still on and the screen is still off. 
So is there a fix for this problem, or is just a quirk of ubuntu?

---

### Post by BennBuntu on 2009-01-31
I remember reading something about ethernet card not shutting down, maybe check out [http://www.lesswatts.org/]("http://www.lesswatts.org/") if you haven't already. It mentions turning off Wake On Lan to save a few watts.

Something I see mentioned at thinkwiki.org is usb suspend, do you have anything power hungry connected to USB?

---

### Post by Naughty 240 on 2009-02-02
Nope i very rarely have anything usb connected to the computer. I have wake on lan turned off in BIOS aswell.

---

