---
title: "manual grafic card configuration"
date: 2010-12-12
forum: Hardware
---

### Post by der-seemann on 2010-12-12
**Ubuntu @ Powerbook G4 400mhz** 			
 			 			 		   		 		 		Hello,
after weeks of searching the net I still have this open problem...
What's about:

I'm trying to install Ubuntu (or lubuntu) to this old Powerbook [http://en.wikipedia.org/wiki/PowerBo...m_PowerBook_G4]("http://en.wikipedia.org/wiki/PowerBook_G4#Titanium_PowerBook_G4")  with 400mhz PPC CPU.
I got it instslled and can use the terminal, but can't get the xserver running!
The problem is the display is verey sensitiv with correct resulution and  frequency, if it is not OK, it will not show enything (well, some  colors like northern lights :smile: but nothing else )
I can login using the keyboard and hear the logon sound of gnome. but of cause i cant see anything :sad:
I got no external monitor for testing.


Now the big question:
how can i setup the grafic card in the actuel version of ubuntu?
here i found some info, but it's not working anymore with 10.10
[http://wiki.ubuntuusers.de/Archiv/Ap...ok_G4_Titanium]("http://wiki.ubuntuusers.de/Archiv/Apple_Powerbook_G4_Titanium") 
here i found the following datas for the screen:
resolution: 1152x768[INDENT]horizontal
    31-46  vertikal
    50-70 
[/INDENT]Thx for your help!!!
David

---

### Post by Fafler on 2010-12-12
```
sudo Xorg -configure
```Then edit the configuration file with

```
sudo nano /etc/X11/Xorg.conf
```

Then reboot and, hopefully, enjoy :-)

---

### Post by der-seemann on 2010-12-12
I tried this, but it didn't work :-(
i had a xorg.conf file that worked under a native debian install, but ubuntu would not work with it. in fact, it does not seem to care about this file at all...
with debian i could change some settings and that made the strange colors appear different and in the end i even got a really bad picture. than i logged in and changed the resolution / freuence under gnome and got it working quite well.
but ubuntu shows always the same color pattern, whatever i have tried so far!

---

### Post by Fafler on 2010-12-12
Maybe you should try a more Linux-on-PowerPC minded distribution, like Yellow Dog Linux. Or at least talk to some people who knows about the hardware it's build on.

---

