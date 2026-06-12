---
title: "System Monitor problems"
date: 2010-01-24
forum: Hardware
---

### Post by aljachimiak on 2010-01-24
I'm having problems viewing the system monitor in gnome...

[IMG]http://i200.photobucket.com/albums/aa261/aljachimiak/sytemmonitorproblem.png[/IMG]

The entire window isn't drawn correctly...

I'm not sure if this is a hardware/driver issue or a gnome problem.

It's a Toshiba 1905-S301 laptop if you are curious

Thanks for any help!

---

### Post by aljachimiak on 2010-01-24
FYI - system notifications like battery discharging and others are also shown pixelated like that...

I can't really tell what the notifications are but they usually happen when I plug-in/unplug the laptop.  There are others that are related to Wifi but that happens less frequently...

---

### Post by aljachimiak on 2010-01-26
<Bump>

Any thoughts?  I installed KDE and thought it might help...But it was much worse...

---

### Post by t4thfavor on 2010-01-26
You need to enable or disable direct rendering on your video card. i cannot remember which, but it's one or the two.

---

### Post by aljachimiak on 2010-01-27
Thanks for the reply...

Direct redering is on, so I tried turning it off.

However, xorg.conf isn't in my /etc/X11 folder...

when I try 
```
sudo nano /etc/X11/xorg.conf
```
I get a new file...

Any thoughts...

---

