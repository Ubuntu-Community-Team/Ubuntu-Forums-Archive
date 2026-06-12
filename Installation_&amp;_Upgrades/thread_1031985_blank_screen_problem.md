---
title: "blank screen problem"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by ginderhulk on 2009-01-05
i am new to linux and i just installed ubuntu 8.10

so i made the live cd, ran it, tried the demo, liked it, installed it
then it told me to restart
so i obliged
here is the problem
the ubuntu loading screen comes up
it finishes loading
then the screen goes off and on twice
and then there is a blank black screen

so no splash screen i can hear the ubuntu start up sound
one time i even tried logging in with the screen blank
and i heard the sound the ubuntu plays when it starts up but no display
also i tried the crtl alt f1 but that nothing changes
i have tried fixing some xserver thing but that didnt do anything either

so if anyone could kindly help me it would be gladly appreciated
also keep it simple i am no that linux code savvy yet

i would tell you all my specs if i knew them or how to get them

---

### Post by lemming465 on 2009-01-19
Initial installs of intrepid ibex can have video glitches, many of which are fixable with later updates.  You are probably among them.

By default there should be a "rescue mode" item in your grub boot menu, which would boot to a single-user text console running a shell as the root user.  If you have that, and try it, do you get to a visible "#" prompt where you can type commands?  If so, try this```

/etc/init.d/networking start
apt-get update
apt-get upgrade
dpkg-reconfigure xserver-xorg
```
If not, boot the live CD, open up a terminal windows (Applications -> Accessories -> ...), and send us the output from **sudo lspci -vv**

Another option would be to install ubuntu 8.04 "hardy heron" instead; it has a less bleeding edge X windows implementation and might do better on your hardware for now.

---

