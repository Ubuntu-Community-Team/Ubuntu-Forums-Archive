---
title: "Asus Eee PP 1215B - AMD Unsupported hardware"
date: 2012-06-03
forum: Hardware
---

### Post by Dragon2012 on 2012-06-03
I'm owner of Asus Eee PC 1215B with AMD C-60 processor and Radeon 6290 on it. I have Windows 7 and Ubuntu 11.04 installed. I have an issue on Ubuntu 11.04 - I've installed additional graphics driver (ATI/AMD FGLRX) and now everything works fine, but in the right screen's corner I have a notification with "AMD Unsupported hardware" message. If I delete the additional driver, the notification disappears, but then I don't have application list bar at the left side of the screen and the graphics' and effects seems to be at a lower level. What should I do now, to save UI with shortcuts' list at left side of the screen and don't have this annoying notification ?
PS: I'm totally new to Ubuntu :).

---

### Post by Redblade20XX on 2012-06-03
Here's a link to a wiki that should get you on your way! It should be beginner friendly so just take some time reading it.
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

-Red

---

### Post by DGINSD on 2012-06-04
I installed my radeon/AMD drivers manually following the instructions here [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29")  Mostly to be sure I had the most up to date one. Be sure to verify your card/chipset is still supported, also if you do choose to re-install manually start with the "Removing Catalyst/fglrx" first as it won't work properly if you don't start with a clean slate so to speak.

If I recall correctly installing the fglrx driver through jockey (the "additional drivers" GUI) with Ubuntu 11.10 I had issues, leading me to the manual install method and above instructions. Just curious, how come your using 11.04 rather than upgrading to 12.04, seems to me a lot to things have been fixed and upgraded making it definitely worth the trouble

---

### Post by Dragon2012 on 2012-06-04
Oh, please, don't ask why I'm using 11.04 instead of 12.04, I had o lot of troubles with installing Ubuntu, everything here [http://ubuntuforums.org/showthread.php?t=1991107](http://ubuntuforums.org/showthread.php?t=1991107), so I'm pleased Ubuntu is finally working :).
Thank you guys, I'll try this guide later, we'll see how will be the outcome :).

---

### Post by DGINSD on 2012-06-04
I just actually stumbled upon this [http://ubuntuforums.org/showpost.php?p=10950714&postcount=334]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334") this morning, sounds exactly like your issue, so it my be more relevant, though the first post may work for you as well. Regardless of which you follow, be sure to remove all traces of the previously installed driver first.

---

