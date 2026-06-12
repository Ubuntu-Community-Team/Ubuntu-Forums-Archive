---
title: "no sound on ubuntu 7.04 but good on 6.06"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by lian1238 on 2007-08-22
Hi all.
I am using an Acer Aspire 5583NWXMi laptop. I have 2 Live CDs, Ubuntu 6.06 and 7.04. Somehow, there is no sound on Ubuntu 7.04 but 6.06 detected a HDA Intel (alsa), which works right away. 7.04 detected HDA Intel (alsa) and Realtek (oos), but no sound at all.

Is there a possible solution to this? Install 6.06 and upgrade to 7.04? Install 7.04 and use drivers from 6.06? (I'm just guessing.)
Any help is much appreciated.

---

### Post by nosrednaekim on 2007-08-22
no, an upgrade won't work since the drivers are in the kernel which will inevitably be upgraded.

---

### Post by lian1238 on 2007-08-25
I have just downloaded Ubuntu 6.10 and now running live from cd. Still no sound.
It must be something that happened between 6.06 and 6.10.
If anyone knows how to fix this, please reply. I really want to migrate to Ubuntu from XP.

My usb headphones work, if that's any help.

---

### Post by lian1238 on 2007-09-01
I have got it!!
Turns out, all I had to do was unmute the "surround" from the default, HDA Intel (ALSA mixer).
Thanks to [http://paulsiu.wordpress.com/2007/06/25/linux-on-a-acer-aspire-3680/]("http://paulsiu.wordpress.com/2007/06/25/linux-on-a-acer-aspire-3680/")
I bet this is the solution for all acer aspire laptops with ubuntu 7.04 and 7.10.

---

