---
title: "Problems with display........"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by kwboom on 2009-01-01
HI there I just installed Ubuntu 8.10 and everything was just fine untill I installed the nvidia drivers and now my screen looks fuzzy and I can't even get my resolution right.  I need to set it to 1366 x 768 for my screen and I can't do that if I run the drivers said to run my card.  I really like to have the compiz and other effects going but my screen really looks bad if I enable the drivers.   What am I doing wrong??????????????

---

### Post by redneckProgrammer on 2009-01-02
I too have had issues with the nvidia restricted drivers.  Some video cards seem to required a custom driver or install process.  I would suggest using the restricted drivers manager to deactivate those drivers.  Then search the forum with your video card model (i.e. 8800gt drivers).  

Or another possible solution.... I had an nvidia 6200 on one pc.  The version 177 drivers (that showed up in the driver manager) caused me similar issues, so I tried the version 173 drivers  (that also showed up in the driver manager) and they worked.

---

### Post by gettinoriginal on 2009-01-02
This is an excellet tool for checking you system capabilities for compiz:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

And this one answers alot of questions:
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by kwboom on 2009-01-04
Thankyou for your answers, I guess I have a search on my hands.....:popcorn:

---

### Post by kwboom on 2009-01-04
Well I installed the restricted driver that it told me to use and I got my screen working at 1280x800 at 60 Hz, not looking too bad but a bit on the fuzzy side.   The only problem now is that it will not let me save the settings in the Configuration file.  I get this message.......

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.


What do I have to do to have thies settings load when I start up????????

---

### Post by kwboom on 2009-01-04
Well I figured out how to save the config file.   You must first run the nvidia-settings from the terminal as root, than it will save.  I still have the problem with the screen being a bit fuzzy.  It is just fine before I installed the drivers but after it is a bit fuzzy.:confused:

---

### Post by kwboom on 2009-01-04
Ok I think I have the resolution set to the best I can but when I restart my computer it will default back to something else and I have to change it everytime I load Ubuntu.  

How do I set my current display as default?????

---

