---
title: "Nvidia Proprietary Drivers disapeared"
date: 2008-08-05
forum: General Help
---

### Post by puhhy on 2008-08-05
Hi. I installed ubuntu Hardy Heron a few days ago. Spent the first couple days getting everything set up the way I wanted it. Got my themes and icons all nice and sexy and all that good stuff... Had my dual monitors working properly. Had the advanced desktop features working. Everything was going smooth... until last night... 

I have a dual boot windows xp and ubuntu box. I logged into Ubuntu when I got home from work last night. Dorked around with it a little bit, but didnt really make any changes that I can remember. I had been trying to go to Screen Resolution because I wanted to try to get it to stop having stuff (like the login window when I lock the screen) show up half on one screen and half on my other. But I kept getting an error saying X Server didn't support RandR and couldnt change settings and real time or something to that effect... so I wasnt able to really change anything.

Then my fiance and I decided to play some wow, so I rebooted the box and got onto my Windows and played some wow... when I rebooted again to return to ubuntu all of my problems began. Immediately while booting up I noticed my second monitor didnt come up. Then upon loggin in I found that my resolution had been reset to 800x600. My monitor and Video Card werent really being recognized the same way they had before... so I first attempted to go to System>Nvidia settings; however when I tried that it said I needed to run nvidia-xconfig.

so i ran sudo nvidia-xconfig
and it gave me the normal results that say backup created as such and such and configurations made to such and such... but still didnt work. 

so then I checked to see if the Nvidia Proprietary drivers were still set to enabled. When I checked that I found that it was no longer even a selection... so id imagine that is related and quite possibly the core of my problem. 

Any ideas? Anyone seen this before? I realize everything was above was a ramble and in order for me to get any real help Ill probably need to be on my computer at home so i can provide information directly from the computer, but I was just hoping I could at least get some information so I can be ready to attack this issue head on when I get off work.

Thanks!

---

### Post by renzokuken on 2008-08-05
Did you update the kernel just before any of this happened?  Sounds like your xorg.conf might be screwed though, and is loading a generic driver such as VESA instead of NVIDIA. Could you post your xorg.conf below?

```
gedit /etc/X11/xorg.conf
```

---

