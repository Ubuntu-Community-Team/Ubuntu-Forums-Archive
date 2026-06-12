---
title: "During the install of 12.04 beta2, crash when entering user info"
date: 2012-04-04
forum: Hardware
---

### Post by versvs on 2012-04-04
Hi,

I've been trying for a few hours now to get the new 12.04 beta 2 up and running in my laptop. I've found a few problems :)

Most of the problems are related to the graphic card, an unfriendly GMA500 that kept me locked in Maverick... but Precise beta 2 promises to work for my graphic card, so I wanted to try.

1. Though right after boot up the screen appears splitted in two, as soon as you choose a language and "TRY" everything goes smooth.

2.a. The install process begins fast. The copying of files is also fast. But we're now approaching to the error.

2.b. While the files are being copied, a series of dialogs where you enter basic info (keyboard layout, etc.) ask you for the data of the first user. Here comes trouble. I can select a city and a keyboard, but when I try to fill the info related to the user and the machine (user name, machine name, passwd), the dialog takes an infinite time to continue...

... and, in fact, never goes beyond that.


I've tried several times trying all posible situations in the dialog: trying to advance while still copying, after copying, with "ask for passwd to log in" and also without that option.


The result is always the same. My install doesn't finish and I'm forced to be back... to Maverick. Again.


Any ideas would be very appreciated.

Thanks!


Edit. OK, I realized that if this is not a gma500-related issue, maybe this is not the correct forum for me to post. Sorry.

---

### Post by ewz on 2012-04-04
Hi 
Are you installing from a CD or USB Stick? 
I have had a similar issue crashing just after filling in the user info 

By default making a bootable USB it adds persistent storage
I found that if I made the USB Drive without persistent storage it worked fine 

Also you may want to re download the iso just to make rule out corruption 

Hope this helps :)

---

### Post by versvs on 2012-04-05
Thanks ewz,

I was using a USB Stick with verified md5sum :)

I solved the issue using the alternate install cd.

Now I got a few other (but minor) problems. I still didn't got the login screen properly (the [vt.handoff]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/914311") and  [console=tty1]("https://wiki.edubuntu.org/HardwareSupportComponentsVideoCardsPoulsbo#Psb_gfx_drivers_.28promising_for_Precise_12.04.29") tricks didn't work for me). I can't suspend the laptop, either.

But these are mainly problems inherited from the gma500, and I can't neither suspend the laptop in Maverick :D


Thanks again!


Ninjaedit: Changed html markup for bbcode markup. lapsus! :D

Edit (2012-04-06). Finally, the console=tty1 trick is fine. It was my fault, was editing the incorrect line. Sorry. The problem suspending the session remains, though.

---

