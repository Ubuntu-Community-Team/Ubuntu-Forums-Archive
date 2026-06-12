---
title: "External Bluray unit won't mount"
date: 2014-11-26
forum: Hardware
---

### Post by nelson777 on 2014-11-26
I have recently bought an ASUS SBW-06D2X-U external USB Bluray unit for my Dell Vostro 3350 i7 notebook. I pluged it as instructed, with an external power source, but the unit just flashes and never gets mounted.

The most strange thing is that I tried it on 2 computers at my work (12.04 and 14.04) and it worked flawlessly.

I used a USB voltage/amperage tester to check the ports and they have similar reads at my home and at work.

Checking dmesg I see that Ubuntu recognizes it and then immediately disconnects. When I first started looking for this issue I was using Ubuntu 14.04 64bits and in order to try to solve this I upgraded to Ubuntu 14.10 64bits but the problem continued.

Dmesg output: [http://pastebin.com/1WWpPk8r](http://pastebin.com/1WWpPk8r)

Any help appreciated. Thanks.

EDIT:

result of 'lsusb -v -d 13fd:0940':

[http://pastebin.com/KAc4VMxW](http://pastebin.com/KAc4VMxW)

EDIT 2:

I had installed nvidia proprietary drivers (fglrx) from Nvidia site. They where compiled on my machine. Removed them. Installed Nouveau. Same thing. 

-Nelson

---

### Post by nelson777 on 2014-12-22
I finally made it work. It was an energy problem. I have a notebook "board" which serves as ventilation and usb hub. I p&#314;ugged 2 usb hubs to it with keyboard and trackball attached to them and I was trying to connect the Blu-ray unit to one of the hubs. I disconnected all this, connect everything to an energized hub plugged directly to the notebook and it finally stabilized and mounted correctly.

---

