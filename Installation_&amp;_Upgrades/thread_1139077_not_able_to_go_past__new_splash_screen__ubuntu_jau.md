---
title: "not able to go past  new splash screen  ubuntu jaunty 9.04  64-bit"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by milio1401 on 2009-04-26
:( Hi guys i have the  next problem i today i installed ubuntu jaunty 9.04 64-bit,and everything  went smoothly,i don't exactly know what happened the firs time i installed  jaunty i did sudo apt-get update to update some  of the packages,then i installed  ATI binary x.org drivers and  alsamixergui and gnome alsa mixer and i restored  my bookmarks and add-ons that's all  i did i swear,my my computer  had previously detected   my graphics card and the  generic driver icon popped up,so i just rebooted,and when you see the new splash screen i kinda loaded up then kinda blinked again and maybe two more times  as it was doing this  the ubuntu icon and the little bar below it changed  colors and kind of turned green,then i'm like ok i guess i screwed up somehow,so i decided to do a clean install again,everything went very smooth until i got to the point where  i installed the ati x.org drivers and alsamixer that's when it happened again,i'm not able to see my desktop it freezes  and all i see  is the ubuntu logo and loading bar kind of greenish,i think it has to do with the video card,can you please  help me fix this.  :confused:


my video card is ATI radeon HD 3870x2,motherboard Abit IP35 pro

And by the way jaunty looks really really nice,man  i liked  since the fist time i installed on my cpu

---

### Post by milio1401 on 2009-04-26
somebody there?,please can  anyone help me out with this problem?,i'm running my computer from the live cd,i can't  access my desktop or anything like that,unless i use the live cd,also when it reboots and you press the esc key  i've gone there too,and and pressed  try to fix  broken packages and  the other ones as well,but nothing  happened.i don't know what to do,and i  don't want  to start messing around with it because i can make a mess.

---

### Post by milio1401 on 2009-04-27
ok i was able to access my desktop by entering  these commands  

sudo apt-get remove --purge xorg-driver-fglrx

sudo /usr/share/ati/fglrx-uninstall.sh

can someone tell me how i can install my graphics card drivers please

---

### Post by milio1401 on 2009-04-27
well i think i decided to upgrade i little to soon  at least for my system, i think i gonna go  back to 8.10 fro a month or two  more before  upgrading again.
Don't bother to reply i'm going to be using intrepid.if the mod can delete my post it's fine,it's just using space.

---

