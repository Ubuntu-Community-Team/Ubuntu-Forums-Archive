---
title: "ATI HD3600 cannot boot with Live or Install"
date: 2008-07-14
forum: Hardware
---

### Post by theedudenator on 2008-07-14
I have 2 HD3600 video cards with crossfire cables.

I have been trying to load ubuntu.
I tried to install but after the "ubuntu" screen, the monitors turn off.

I tried to run it live also, and the same thing.

It seems like when it tries to start X the video cards are not active.

---

### Post by Rocket2DMn on 2008-07-14
The LiveCD has limited support for video cards, and with cards that new, you will probably have to use the alternate install cd - it doesn't have a live session, just a text based installer, but it is intuitive and easy to use.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.

---

### Post by theedudenator on 2008-07-16
I tried that but was not able to ever get it to boot after that.

Dunno if it was a Grub problem or cause I tried the 64bit version.

I installed PClinux0S today with no issues...  so I dunno why Ubuntu is giving me problems.

---

### Post by Rocket2DMn on 2008-07-16
For Radeon HD cards, you need the radeonhd driver or the correct restricted drivers.  You can use EnvyNG to get the restricted drivers by either using the safe mode GUI or by doing it from a tty.
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A) (you would want EnvyNG core if you were to install from a tty).

---

