---
title: "ATI Dual Screen with Laptop Screen and External Screen"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by nemis on 2007-05-06
I have managed to get dual screen working except that my laptop screen is det default screen. I would like my external screen to be the deafult one (containing the the GNOME panel etc). Anyone know how to change the default screen?

I have an ATI graphics card and I got the dual screen working by simply typing the following command:
```
sudo aticonfig --desktop-setup=horizontal,reverse
```

---

### Post by jack1254 on 2007-05-06
If nothing is available in the man pages/documentation for the command you ran, check out this page with information on a few methods of getting dual screens working:
[http://ubuntuforums.org/showthread.php?p=1773710](http://ubuntuforums.org/showthread.php?p=1773710)

With my Radeon 9600, MergedFB works great.

---

### Post by Ailbe on 2007-08-15
I could really use some help with a similar problem.  I have an HP nw8240 laptop with an ATI MOBILITY FireGL V5000 graphics controller with 128 MB of video memory, and an HP1740 LCD screen.  I have read through documentation, and gotten my laptop screen resolution issues working, even have both monitors coming up now.  However, I can't get the screens setup the way I want them.  Instead of having the screen extended across both monitors, I can only get the displays to mirror each other.... **EXCEPT** at the login screen.  The login screen is setup exactly how I like it...  I'm very new to Linux (but have been in windows operations for years now)  I know I'm probably missing some config file that is setup properly somewhere but when my home directory comes up at login is over writing those initial settings?  And I'm just not familiar enough with linux to find where.  

One thing I do remember when I was setting this up, I was unable to run a certain command under my login, I had to su to root in order to run it.  I'm thinking maybe this setup root to extend the screen and my settings remain mirrored?  I'm somewhat at a loss and looking for some help before I dive back into another couple hours trying to figure this out.

Thank you.

---

