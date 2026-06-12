---
title: "celeron m and speedstepping"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by melto on 2006-01-27
hello!
can anybody tell me, if it is possible to make an ubuntu kernel support speedstepping with a intel celeron m processor? i have got an ibm thinkpad r50e and saw an article about speedstepping the processor. maybe you can tell me some more howtos, if that is possible.
melto

---

### Post by darm on 2006-01-28
AFAIK celerons don't support speedstep. Could you give a link to that article?

---

### Post by mael on 2006-02-03
echo "p4_clockmod" >>/etc/modules

reboot or:
modprobe p4_clockmod
/etc/init.d/powernowd restart

you can check it with
cat /proc/cpuinfo|grep -i mhz

---

### Post by sixsixone on 2006-04-14
[QUOTE=darm]AFAIK celerons don't support speedstep. Could you give a link to that article?[/QUOTE]

I worked for Intel...and can confirm all modern celerons have SpeedStep implemented under Windows :cool: 

Having said that I can't get any to work under Ubuntu Breezy... Only a matter of time i guess.

---

