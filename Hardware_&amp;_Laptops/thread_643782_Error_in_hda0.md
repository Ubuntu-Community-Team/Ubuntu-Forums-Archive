---
title: "Error in hda0"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by BmwStreetRacer on 2007-12-18
Hello! 
I need some help, i'm running Ubuntu 7.10 on my HP DV6149eu Laptop, and yesterday, i was on the Console running:

Code:
sudo aptitude update 

Code:

sudo aptitude upgrade 


On the second command i was getting this message:

[2000-xxxx] hda0: drive not ready for command

And it continued all day long until I shutdown the PC :(

Can this be fixed?



Thank's

---

### Post by hihihi on 2007-12-18
hi there,

and now? after turning on the pc? still the same?

---

### Post by BmwStreetRacer on 2007-12-18
I booted normally but on reboot it get's stuck :

[B][ 1939.316000 ] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1979.356000 ] hda: drive not ready for command[/B]


It stays scrolling down the screen with these errors :(

---

### Post by hihihi on 2007-12-18
hi,

it can be fixed probably,
the 1. question is: what kind of soundcard do you have?
if u dont know type this in terminal:
$ sudo cat /proc/asound/card0/codec\#*
the first line tells u what soundcard / driver u have.

---

### Post by BmwStreetRacer on 2007-12-20
Hi my Driver is:  Conexant CX20549 (Venice)


:)

---

