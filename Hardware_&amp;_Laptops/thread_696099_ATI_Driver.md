---
title: "ATI Driver"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by phoenix5002 on 2008-02-13
I am having a little difficulty with drivers.

My first question is, is it possible to rollback drivers in ubuntu?  If not, then is it possible to back up certain files before updating drivers so that I could revert back to the previous state if I encounter problems?

The driver I origionally have when I install Ubuntu has a few issues.  Screen savers run slow and when I move the screensaver selection window around sometimes the screen leaves a trail, and if I move another window ontop of it the screensaver will render ontop of that window.  No big deal really.  Another issue is that Armagetron Advanced constantly crashes saying (core dump) on the terminal.  However...I get around 60FPS playing most other games.

When I upgrade to the linux mobility drivers for ATI it fixes all of the above issues except for the Armagetron crashing, and my framerate in games drops to about 20-30FPS.

I then tried using Envy which said it didn't support my card or something like that do I want to try anyway?  and I said yes, and it screwed up my xServer configuration, so I reconfigured and then ALL of the bugs were gone, no screen saver problems no armagetron crashes, but my framerate in games took a massive dive to 12-20FPS.

The wierdest thing I noticed is when Game FPS would be decreased due to a driver update screenSavers seemed to run faster and smoother.

I currently have a fresh installation of Ubuntu due to several other issues, but anyway I'm back to square 1 with my origional video card driver.
So what do u all think?  My laptops video card is a "Radeon IGP 345M".
Are there maybe unofficial drivers that are better?  Should I try Envy again but BEFORE I install ATI's linux drivers?

---

### Post by bliffle on 2008-02-13
Good questions. I'm having problems with the ATI Radeon mobility X1300 card on my IBM Thinkpad T60 laptop, and I don't know what to do next. I'm cautious about just installingcandidate drivers and trying them out without having a way to back a driver out. Also, it would be nice to be able to list characteristics and dates and revision levels of drivers.

---

### Post by astrauch1968 on 2008-03-12
I just installed ubuntu 7.10 on a t42p. When I installed the ati driver from the restricted drivers tab, I was able to undo the thing by removing the checkmark again from the restricted drivers tab.
I do not know if the same thing works when you install the ati restricted driver without using the restricted drivers tab.

---

