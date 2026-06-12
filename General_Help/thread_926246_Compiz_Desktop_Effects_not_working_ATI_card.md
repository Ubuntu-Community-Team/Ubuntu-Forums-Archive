---
title: "Compiz Desktop Effects not working ATI card"
date: 2008-09-21
forum: General Help
---

### Post by tommygunner on 2008-09-21
I finally got my ATI Radeon 9550 card driver working in Ubuntu 8.04. Now when I run compiz-check I see that I'm using the fglrx driver and it shows "Ok" for everything.

When I run "fglrxinfo" I see Radeon and not the dreaded Mesa drivers.

However, when I enable some effects like wobbly windows and others, I don't see anything happening. I'm going to re-install Compiz and see if that fixes it.

---

### Post by tommygunner on 2008-09-21
I got it working now! I ran the compiz command and now it is working. I thought it would run command automatically once you load the settings manager but I guess not.

---

### Post by syphon1 on 2009-03-14
How did you get your ATI radeon 9550 to work. I've put like 20 hours into getting it to work and nothing. I have a fresh install of Xubuntu. I tried Gnome and liked it but couldn't get my video card to work. I tried Kubuntu and the fonts were HUGE and couldn't find out how to get them smaller! I've now went to Xubuntu hoping I could get it to work. If it does the same thing as Kubuntu I'm going to just switch back to Gnome and hopefully somebody could tell me exactly how to get it working.

---

### Post by tommygunner on 2009-03-14
Well, I'm running Ubuntu 8.10 now. It recognized the card right away after installing Ubuntu. The problem was after I tried to select newer drivers after the installation. I just had to stick swith the original ones.

---

### Post by Forlong on 2009-03-16
> **syphon1 said:**
> How did you get your ATI radeon 9550 to work. I've put like 20 hours into getting it to work and nothing. I have a fresh install of Xubuntu. I tried Gnome and liked it but couldn't get my video card to work. I tried Kubuntu and the fonts were HUGE and couldn't find out how to get them smaller! I've now went to Xubuntu hoping I could get it to work. If it does the same thing as Kubuntu I'm going to just switch back to Gnome and hopefully somebody could tell me exactly how to get it working.
The desktop environment in use has nothing to do with hardware detection and/or driver issues, so it's absolutely irrelevant in that case if your are using Ubuntu, Kubuntu or Xubuntu.

Please post the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

