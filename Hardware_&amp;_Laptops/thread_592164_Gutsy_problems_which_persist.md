---
title: "Gutsy problems which persist"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by chronographer on 2007-10-26
Hi everyone

So after a few weeks of gutsy use, there are a couple of problems which I still encounter.

a) Firestarter   [[COLOR="Blue"]launchpad bug report[/COLOR]]("https://bugs.edge.launchpad.net/firestarter/+bug/120445")  My report is near the bottom, with attached error/crash log.

This consists of Firestarter running fine after I install it, it does crash occasionally, but this would be a minor problem EXCEPT that when I restart with firestarter installed, ubuntu won't start, seems to be a conflict between firestarter and my wireless card (a ralink rt73) which worked ootb btw, for a few days, then I needed to install drivers manually.

b) My Ricoh R1 digital camera, which always worked in previous debian/ubuntu installs, now appears to not work with gutsy. This could probably be fixed if I could roll back gphoto2 and library, instead of using the gutsy bleeding edge versions. I have documented this bug here: [[COLOR="Blue"]gutsy gphoto problems[/COLOR]]("http://ubuntuforums.org/showthread.php?t=565018") Can't find anyone else with this problem, can't fix it myself, so currently importing photos on my feisty laptop and copying them across!

c) User switching.  When I switch users, I usually, but not always, get a funny green log-in page and then a washed out purple tinged desktop. Strange!  This can be fixed usually by switching to a virtual terminal (ctrl alt F1) and back (alt F7).

d) Lastly, running apps in crontab was working, by seting display (DISPLAY=:0.0 /usr/bin/deluge)  and now it is broken somehow, so I get this message if I try that command in a virtual terminal "Xlib: connection to display ":0.0" refused by server"  or something similar.  This seems to be the same error which prevents me from running x programs over ssh from my laptop???


So to wrap up, I hope someone out there can help me with at least one of my 'issues' and if anyone else has a similar prob, post too, and check back, maybe we can all fix these things together, make things better for everyone!!

a side note, with the next Ubuntu (hoary), as its long term support, be quite so bleeding edge as gutsy is? If so, the long term support part of it will be still squashing bugs right? I finally understand the attraction of debian's stable distro, while a little outdated in some ways,even on release it is rock solid.

Thanks for everything.

agl

---

### Post by chronographer on 2007-11-10
bump...

gee. I was kinda hoping this would get a bit of attention at least eh?  

Oh well, thanks for looking, all you people who do!

---

### Post by chronographer on 2007-11-19
so just an update here:

a) firestarter still dies in the **** whenever i boot up with it installed.

b) the camera doesn't work, some folks from gphoto dev said it may be due to the kernel? too deep for me!

c) user switching still results in green screens, purple virtual terminals etc. but can be fixed by switching between them.

d) i have found a solution to DISPLAY=:0.0 not working, i needed to add myselt to the list of people able to use x, in the Xauthority file or something, by using "xhost + <username>" yay!

I must say that while I love compiz with its wobbly windows, transparencies and pretty transitions, it still breaks a lot of things... I am quite sure compiz is the one breaking things in c) and it causes a 'white screen of death' sometimes too. This can be fixed with "DISPLAY=:0.0 metacity --replace" in a virtual terminal (ctrl alt F1) and then swapping back to F7 and ctrl alt back spac'ing to restart X.

bye now

---

