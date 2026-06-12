---
title: "a few problems with my presario cq60-215dx"
date: 2010-03-06
forum: Hardware
---

### Post by duble08 on 2010-03-06
hey guys - so i've been a micro$oft junkie since the age of 4, messing with dos prompts and whatnot before i could even officially read.  computers have always kind of been my thing... recently, to make a long story short, i got fed up with micro$oft, for TONS of reasons, and i've been desperate to try something new - so now i have ubuntu 9.1!  so far i love it, and i don't ever plan on going back - but with that said, there are some issues i'd like to address that maybe you linux pro's could help me with, since i'm entirely new to a linux system (i did mess with red hat a bit in the late 90's, but gave up early... i'm still very new)

First, i have some issues with the video in my machine, and i think i've found where the problem is from, but not what causes it.  my machine is a compaq presario, model cq60-215dx. it has the nvidia graphics card model 8200m.  the issue i have with it is that there's two driver options under the hardware drivers section under the admin menu - drivers 173 and 185....

drivers 173 load up fine, but i get this glitching problem while scrolling thew web pages with images, and emails in empathy, and texts in synaptics manager for example - it always happens. it looks as if it's stacking part of the page on top of the other.  i've been using this driver because i got a "driver fail" error everytime i booted up with the 185 driver.  the glitching annoyed me so much, i tried to find out what was wrong with the 185 driver.  the 185 driver worked when i fresh installed ubuntu, but when ever i'd reboot it would make me boot into ubuntu's "safe mode" so to speak (as a winblows user that's how i'd recognize it) which would then leave me to roll back to the glitchy 173 driver if i wanted my graphics acceleration.

I've found the problem (kind of) with the 185... i have an external usb seagate 1tb hard drive.  apparently, if it's plugged in while booting ubuntu, the 185 nvidia driver fails... if the hard drive is unplugged, the 185 nvidia driver loads just fine.  i can then plug in the hard drive later and access it as needed.  this doesn't pose that big of a problem to me, all though it was frustrating to try to figure out why the drivers would only sometimes work.  so just a heads up to those that are having the same problem, and hopefully there will be a fix sometime soon...

Onto my other issue, and my appoligies if i'm posting this in the wrong spot, but i'm a WOW geek... World of Warcraft to those unfamiliar with the term... wow used to work great for me under WINE, but all of a sudden, i'm getting errors... it appears i'm not the only one with these errors, but i feel i'm the only one that can't resolve them.  Right now i'm getting a permisions error... it says: 

Details: Failed to change to directory '/home/jeff/.wine/dosdevices/c:/Program Files/World of Warcraft/' (Permission denied)

i've read online that some people have made a script on how to fix this, and i've also read that my version of WINE has also fixed the error itself... obviously the error still exists in the newest version of WINE (or it's a ubuntu problem) and i've tried the script that someones posted previously about a fix.  the script contains these codes:

#!/bin/bash
clear
wine "/home/jeff/.wine/drive_c/Program Files/World of Warcraft/wow.exe";
chmod 755 "/home/jeff/.wine/drive_c/Program Files/World of Warcraft/" -R

when i run this script, it either:
A.  gives the same permisions error, or
B.  completely restarts ubuntu (goes out to terminal, reloads gnome and asks for me to log in again)

i havn't had any of these problems before until ubuntu told me there where updates available, and i chose to install them.  is there a problem with the updates it installed? is there a way to "undo" or "remove" these new updates? are there any other suggestions for a fix to this? i really don't want to go back to winblows, and i don't want to buy a mac.  ubuntu/linux seems to be my solution if i can get everything working ok...

anyways, sorry for the long drawn out explanation of things - i didn't mean to write a novel, but i feel detail is important in troubleshooting...  any help would be greatly appreciated.  if you need any more info on my machine, any specs, errors, whatever you need, please let me know - i'd be willing to do what it takes to keep ubuntu/linux as my one and only OS.

Thank you!!

---

