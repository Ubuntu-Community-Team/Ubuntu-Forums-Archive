---
title: "Karmic intel GMA 950 not working"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by iecltd on 2009-11-02
recently upgrade to 9.10 from 9.04 
my video is a Intel GMA 950 on version 9.o4 I needed to add the intel repository and install a new 2D driver this worked well but on upgrading the video has reverted to 800x600 and I cannot find a suitable 2D driver.
Can anyone point me in the right direction.

---

### Post by RuarriS on 2009-11-02
I did a clean install, and all I get is a black screen..

---

### Post by anarkae on 2009-11-02
I upgrade from 9.04 to 9.10 and when I start gnome I get a white screen.
(I don't get the white screen on KDE)

I had some problems with my intel gma 950 when I upgrade from 8.10 to 9.04.

the same to this post: 
[http://ubuntuforums.org/showthread.php?t=1080992](http://ubuntuforums.org/showthread.php?t=1080992)

and I solved it by rolling back my drivers.
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I would like to know if I can do a roll back to revert the driver on 9.10.
and how?

---

### Post by anarkae on 2009-11-08
any update?

---

### Post by anarkae on 2009-11-08
I solved my problem!
I just ran:
sudo apt-get install xserver-xorg-video-intel
:p

---

### Post by yknivag on 2009-11-08
> **anarkae said:**
> and I solved it by rolling back my drivers.
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I would like to know if I can do a roll back to revert the driver on 9.10.
and how?

THANK YOU! Finally I am able to view video in 9.04! Fantastic! :) :) :)

I'd be interested to know if this works in 9.10 too before I upgrade.

EDIT: Even Compiz works too now! :)

---

### Post by anarkae on 2009-11-08
On 9.10 I had a problem with this video card.
I got a white screen when I logged in a gnome session.
I solved this with:
sudo apt-get install xserver-xorg-video-intel

---

