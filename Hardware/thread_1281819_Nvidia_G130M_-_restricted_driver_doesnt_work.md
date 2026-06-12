---
title: "Nvidia G130M - restricted driver doesnt work"
date: 2009-10-03
forum: Hardware
---

### Post by skjoldfetter on 2009-10-03
i got a brand new packard bell easy note TR87, with the Nvidia G130M graphics card, and when i install the restricted driver i get 6 tiny mirrored desktops popping up on my screen rather than one.

its the lates ubuntu desktop version.

does anyone have any clue what causes this and/or how to fix it?

thanks :)

---

### Post by skjoldfetter on 2009-10-04
didn't find a bump thread button... so here's a bump :)

i would really love if this worked so i could trash windows vista ^_^

---

### Post by beastrace91 on 2009-10-04
Perhaps try installing a newer driver version as that is a relatively new gfx card (and the hardware driver included in 9.04 is kinda old)

Download the proper driver from [here](ftp://download.nvidia.com/XFree86/) (Grab the 185 or if you are feeling adventurous the 190 driver is in beta and works quiet well at least for myself)

And then install it following the directions [here](https://help.ubuntu.com/community/NvidiaManual)

Hope that helps,
~Jeff

---

### Post by skjoldfetter on 2009-10-04
a newer driver would very likely help, and i've been trying to find a way to do that all day with no luck, and even in your link i come to a dead end when it tells me to edit my xorg.conf, and mine doesnt have the part it wants me to edit... (tried to attach it, not sure it worked)

i have also downloaded the 190's .run from nvidias official page, however when i click it a terminal pops up for a millisecond, without giving me time to see it, and then disapears again.

any further ideas how i could get it installed? :)

---

### Post by skjoldfetter on 2009-10-05
latest attempt, installed envyNG, however it only offers up to the 180 driver. :(


EDIT: downloaded 2 more drivers from your list and one of them works, however it wants me to run it as root, how can i do this?  (sorry for being a bit of a noob :P)

---

### Post by skjoldfetter on 2009-10-06
bump :)

---

### Post by T l2 O J A N on 2009-10-06
I have same problem. :mad:


[http://ubuntuforums.org/showthread.php?t=1284017](http://ubuntuforums.org/showthread.php?t=1284017)

---

### Post by skjoldfetter on 2009-10-07
bump

---

### Post by skjoldfetter on 2009-10-08
well, i successfully installed the latest Nvidia driver (190.36)  (thanks sandy)

but unfortunately it did the exact same thing... so i guess the graphics card is just too new and not supported yet, and ill have to live with vista untill Nvidia release a better driver :(

thanks anyways ^-^
ill just mark this solved for now.

---

