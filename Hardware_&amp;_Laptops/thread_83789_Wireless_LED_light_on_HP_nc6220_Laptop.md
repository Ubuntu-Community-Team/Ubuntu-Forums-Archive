---
title: "Wireless LED light on HP nc6220 Laptop"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by tekmerc on 2005-10-29
Hello,

I installed breezy on my new HP nc6220 laptop. Almost everything worked out of the box! Ubuntu is sweet, I have been using linux since 1996 and nothing has worked this smoothly before. 

This laptop has a switch which turns the wifi transmitter on and off. In windows, if the switch is on, a blue LED turns on (both on the switch and near where the power/hdd led's are). How do I activate this in breezy?

Thanks,

Tekmerc

---

### Post by JLB on 2005-10-29
I have a NC6120. This works for me. I use the ipw2200 driver. I think yours uses the same. Hope this helps.

Wifi Status LED can be made to work easily by creating/editing /etc/modprobe.d/ipw2200. i.e. 'sudo gedit /etc/modprobe.d/ipw2200' add the following text to it, save, and after your next reboot you will have a functioning blue LED.

options ipw2200 led=1

---

### Post by tekmerc on 2005-10-30
Thanks! That worked. I should have found the README.ipw2200 myself

---

