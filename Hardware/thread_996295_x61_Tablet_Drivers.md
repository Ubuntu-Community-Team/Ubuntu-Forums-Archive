---
title: "x61 Tablet Drivers"
date: 2008-11-28
forum: Hardware
---

### Post by norman_069 on 2008-11-28
Hello, I put ubuntu 8.10 on my x61 tablet and it is working pretty good but i don't seem to have any of the drivers needed.  I did a modification to get the tablet working but it doesn't rotate or anything.  I have looked at thinkwiki.org on how to set up stuff but it doesn't show 8.10. would the setup for 7.10 and 8.04 be that same as 8.10.  is there a place to go to get the drivers i need.

Thanks

---

### Post by norman_069 on 2008-11-29
Bump ... anyone?

---

### Post by gus_the_mouse on 2008-12-01
I also am experiencing issues with the Lenovo X61 tablet in 8.10.  In 8.04 I had edited xorg.conf (in addition to installing some things in synaptic), and it was working pretty well.  Then, when I installed 8.10, and opened up xorg.conf, everything was commented out:

```
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "stylus"
#        Option          "Device"        "/dev/input/wacom"
#        Option          "Type"  "stylus"
#        #Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
#EndSection
```

I appreciate any help.

---

### Post by renfrowk on 2009-02-11
I just installed Ubuntu on my Lenovo X61 tablet and would appreciate any help getting the tablet functionality setup.

---

### Post by srilyk on 2009-02-28
[http://blog.aliencam.net/2008/10/ubuntu-810-x61t-tablet-setup/](http://blog.aliencam.net/2008/10/ubuntu-810-x61t-tablet-setup/)

I have an x61 - I just installed wacom-tools and added those sections and it worked on an x restart (I think... maybe a full restart).

My tablet works fine now - just have to get some of the other (screen rotate, auto rotate) buttons working.

HTH

---

### Post by kjgillis on 2009-03-15
Have any of you tried using opengl? I tried running neverball and the graphics are scrambled. I also get a momentary scrambled graphic when menus open under KDE. I checked the KDE hardware tool and I seem to be using the intel driver so I don't know whats wrong. I'm using an X61T with a fresh install of kubuntu ibex.

---

### Post by mixmadmen on 2010-05-07
For any lone googlers:
I can confirm that the [http://blog.aliencam.net/2008/10/ubuntu-810-x61t-tablet-setup/](http://blog.aliencam.net/2008/10/ubuntu-810-x61t-tablet-setup/) fix works for those who upgraded to 10.04 LTS Lucid Lynx, as well as older Hardy Heron installs.


(For whatever reason the upgrade comments out any previous fixes in xorg.conf so just follow the directions on that site.)

---

