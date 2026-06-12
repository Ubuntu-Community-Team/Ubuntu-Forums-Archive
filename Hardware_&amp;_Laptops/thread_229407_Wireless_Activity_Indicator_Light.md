---
title: "Wireless Activity Indicator Light"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by graviray on 2006-08-04
I have Inspiron 9300 from Dell and I just installed Ubuntu. Every thing seems to work except that I'm having trouble making the light that indicates whether the wireless network card is on or not does not work. The wireless card itself works and I can turn it on/off by using Fn + F2 key sequence as expected; it is just that the indicator light do not toggle (it remains off). Some one please help me make this work.

Thanks in advance

---

### Post by Titus A Duxass on 2006-08-04
Does the wireless actually work? Can you ping [www.google.com](www.google.com) or access the forums through a browser?

If yes to the above then forget about the LED.

---

### Post by s0lar on 2006-08-08
The Led can be made to work.
I also own a Dell Inspiron 9300 and where some other distros have problems with wireless card drivers, my 1920*1200 screen, the fact that my hard disk is recognised as sda instead of a regular hda. The needed libata fix to make the dvd drive work fast atcetera. Almost everything worked out of the box. The only things I did where installing mp3, divx support and all that stuff, changing my xorgconfig for vertical scrolling, one thing that also is not enabled by default. Further I installed flgrx for my ati x300, works automatically. I recommend installing laptop-mode and enabling it when battery is on, it gives me more battery life. Also change your kernel to i686 ninstead of i386, it makes it run a bit faster. I did not took the time to compile my kernel, why should I, almost everything works, this rocks.
The multimedia keys like play/pause, stop, forward and backward also do not work, but that is not that big of a problem. I have no idea how to make them work, perhaps because I haven't taken the time to search more about it.
To come back to your led, you need a kernel patch and then it works, I guess you need to recompile your kernel for it, but I could be wrong.
[http://rtr.ca/dell_i9300/kernel/latest/](http://rtr.ca/dell_i9300/kernel/latest/) it's patch number 10.
There is also a fix for the vertical scrolling and some other stuff but most are not needed when using 6.06 allready.
But I do not need the led, since I can see my wireless connection's status in the top corner.
Ubuntu rocks.

---

