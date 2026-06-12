---
title: "[SOLVED] Can not enable wireless in 8.10"
date: 2008-11-16
forum: Hardware
---

### Post by sclewin on 2008-11-16
I installed Ubuntu 8.10 for my wife who haves a laptop with a Broadcom BCM4312 wireless card insided.  I did the usual install of the wireless card driver via the "hardware drivers", but after the install the "enabled wireless" became grey.

I have spent the last week and several hours trying to find a way to get this to work and it will not.  I had the wireless working fine, without trouble, in Kubuntu 8.04, so I know it works.

I tried blacklisting b43 and ssb, it did not work.  I tried installing the linux-backports, that did not only work but killed the computers  Ethernet as well.  I tried re-installing fwcutter and so many other things I can't remember.  When I did /etc/init.d/networking restart I got "Ignoring unknown interface eth0=eth0"

Please help!   I am desperate.  I really don't care what works right now as long as I can get the wireless working.

---

### Post by Henkster on 2008-11-16
Sorry that I can not help you at this moment .. but it seems that you are not the only one with wlan problems in 8.10. See my issues with the acer one as well.. bugger..

---

### Post by Olivier2371 on 2008-11-16
Hi There,

I have an acer laptop and the same wireless. I am running ubuntu 8.04 and I have no problem. On my laptop I have a button to turn on or off my wireless.
The light is on when under windows vista to indicate that it is working.

Under ubuntu the light is off but the wireless adapter works fine.

Good luck.

---

### Post by sclewin on 2008-11-17
Oddly enough I re-installed the driver using the System/Administration/hardware Drivers and it WORKED!!!  I don't know what happened this time;  I tried this twice before.

Another odd thing is that mostly everyone else with this wireless card seems to get it working out of the box.  Even on a live CD.

---

### Post by Olivier2371 on 2008-11-22
sclewin if your problem has been solved please mark the thread as solved, using the thread tool in the forum's menu.

---

### Post by sclewin on 2008-11-22
> **Olivier2371 said:**
> sclewin if your problem has been solved please mark the thread as solved, using the thread tool in the forum's menu.
Thank you.  I never knew the forum had that option.

Just as a note.  This is solved for me, but this thread will be of no help to others as I don't know why the wireless started working.

---

