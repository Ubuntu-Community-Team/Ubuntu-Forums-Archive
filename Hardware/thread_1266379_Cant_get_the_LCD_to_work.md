---
title: "Cant get the LCD to work"
date: 2009-09-14
forum: Hardware
---

### Post by neverthatgood on 2009-09-14
at login it goes to 75 hertz refresh rate, can plug in the crt, login, change the resolution to 1024 x 768, than apply and swithc to the lcd.  When i restart the resolution is back to 12xx x xxx and the lcd doesnt support it.

there is nothing in xorg.conf about resolutions at all.
so i dont know why in the login screen it goes to 75 hertz, and after login it wont keep the previous resolution.  please help.

looked around a bunch, found nothing that helped.

ati9250 vid card
installed linux driver from ati
all the visual effects work

---

### Post by neverthatgood on 2009-09-14
gedit /etc/x11/xorg.conf opens an epty file

if i browse to the folder and open it, it has stuff in it, but i cant save

sudo dpkg-reconfigure xserver-xorg does not have any promps for monitor settings, only keyboard stuff



ok i edited the xorg.conf

and it starts at 1024x768 60hz
but only when the crt is plugged in, if i plug in the lcd, to uses different setting which are incompatable

i need help

---

