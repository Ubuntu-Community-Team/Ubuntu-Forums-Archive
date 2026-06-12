---
title: "AMD 5850, distorted graphics"
date: 2012-07-30
forum: Hardware
---

### Post by spirry on 2012-07-30
Hello everyone!

Yesterday I installed Ubuntu 12.04 and installed and enabled the proprietary drivers for my AMD Graphics. Great so far, really loving it! 

However, when doing anything game-related (Or requireing 3d?) , it seems it comes out really distorted / flickering / weird. 

Or to try to explain more closely:

glxgears runs fine. However, running Starcraft 2 in playonlinux, some frames would sometimes show me the glxgears cogs in some frames, really odd and weird. Has someone else encountered the same issues and have any clue how to fix it? I would love to swap over to linux on full-time.

Thanks in advance

---

### Post by Kreaninw on 2012-07-30
Do you enabled Tear Free in AMD CCC?

---

### Post by spirry on 2012-07-30
> **Kreaninw said:**
> Do you enabled Tear Free in AMD CCC?

I did. Something I read suggested it.
I enabled it before I started my game, I also tried disabling it without any success, same flickering problem :(

---

### Post by oscarivera9 on 2012-07-30
Have you tried the free-open source radeonhd driver?  I was just like you, using the proprietary driver when I first got my RadeonHD 5770.  This was back before I realized that I liked Unity, which means that I was also trying out the (back then new) Gnome 3 desktop environment.  When I would use Gnome 3, the upper panel always looked blurry and the words were not legible, so I decided to find a fix.  I tried disabling the proprietary radeon driver I switched to the open source driver and the problem went away immediately.
Maybe I should mention that I also do a bit of gaming on Linux.  Lately I've been playing Amnesia: The Dark Descent as well as Bastion, both of which were part of the Humble Indie Bundle 5.  I've run into zero problems with the games I've played.  It might be worth looking into:

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Just follow the instructions on that page if you want to try it out.

---

### Post by QIII on 2012-07-30
@oscarivera9 -

The problem with GNOME 3 is a known one and is on the GNOME end.

@spirry -

How did you install the driver?  If from the repo, did you use the "Additional Drivers" GUI method or via the command line?  Did you install the normal driver or the "post release updates" driver?

---

### Post by spirry on 2012-07-31
> **QIII said:**
> 
@spirry -

How did you install the driver?  If from the repo, did you use the "Additional Drivers" GUI method or via the command line?  Did you install the normal driver or the "post release updates" driver?

I installed the drivers using the additional drivers GUI

---

