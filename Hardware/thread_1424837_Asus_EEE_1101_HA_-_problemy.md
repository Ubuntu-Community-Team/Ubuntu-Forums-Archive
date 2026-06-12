---
title: "Asus EEE 1101 HA - problemy"
date: 2010-03-08
forum: Hardware
---

### Post by stuudent on 2010-03-08
Hello!
I have netbook Asus EEE 1101 HA for couple months. I installed ubuntu once, configured and it works. But after using it for several months, some things made working with this netbook frustrating.

I have following problems and I'd be grateful for any help

Most important:

 - after suspend the sound stop working
 - after suspend graphic card (binary Pulsbo driver - Intel GMA500) stops working as it should (ex. using mplayer or opengl appliactions ends freezing the driver, after some timeout and trying to kill processes form another TTY it's possible to use the driver in the limited way - GNOME works ok)

Less important, but also annoying:
 - can't change the frequency, it's automatic - plugged has 1,3 GHz, when battery is almost full 1 GHz, 50% or less battery - 800 MHz. I don't know how to controll it (gnome frequency applet doesn't work)
 - multi-touch doesn't work (when configuring in gnome)
 - button for toggling the touchpad doesn't work neither
 - touching any key on the keyboard leaves entry in syslog:
> evbug.c: Event. Dev: input4, Type: 1, Code: 28, Value: 1
 - I'm using ndiswrapper instead of ath9k (very weak signal), and after turning off wireless by keyboard (Fn + F2) can't turn it on again (maybe I sould restart anything, removing and loading the ndiswrapper module doesn't change anything)

I know that's much, but if you could help me on anything, I'd be more then happy :)

---

### Post by NikUAE on 2010-05-05
Bump
I've blacklisted evbug but something is launching/keeping this running
Forums & searches point only to 

```
/etc/modprobe.d/blacklist.conf
#evbug
blacklist evbug
```

so bump
Lucid TC1100

---

