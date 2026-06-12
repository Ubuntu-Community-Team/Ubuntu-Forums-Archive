---
title: "Possible video driver issues after install"
date: 2005-01-08
forum: Installation &amp; Upgrades
---

### Post by buttonpusher on 2005-01-08
:?: 

I have an PII 350 Mhz PC with an  older PCI video card in it.  I installed Ubuntu with no problems and all the text during the install displayed on the screen of my monitor, But when it completed the install and attempted to boot into the installed OS the monitor screen went blank and when it did display it was more like static on the screen with what I could make out displayed about 2-3 times.

I think it is a problem with the video card drivers (I hope), but as being new to linux I'm not  sure on the steps to correct this.  The video card that I have is a Cirrus Logic CLVGA54PCI and the monitor is a Smile Internaltional CA1507.

If any one would know of how I can get this straightened out I would appreciate it as this will be my linux learning PC.

Thanking all in advance

Buttonpusher 8-[

---

### Post by hardcandy on 2005-01-08
[http://ubuntuguide.org/#gainrootinstallcd](http://ubuntuguide.org/#gainrootinstallcd) shows you how to gain root acess using the install cd and then switching to the installation.
and once you get there, run "xf86config", this will bring up a xfree86 configuration  dialogue. Don't worry about getting everything perfect, the first time I tried it I had to run through it 3 to 4 times to get it to even show a graphical login. I believe your video card is listed in the database. Read everything carefully.
Once you reach the end , save it and then  type "mv /etc/X11/XFree86Config    /etc/X11/Xfree86Config-4". This will rename it to the file the bootup will be looking for. If you can get to the a graphical login you can use the graphical tools to tweak it.

---

### Post by buttonpusher on 2005-01-09
Hardcandy - will give that a shot.  If I'm able to get to the text part of the system first.  I have just tried to re-install the software and it crashed all over the place.  It looks like several parts did not load and install so I will have to clean it all up and try again.  I will try another video card before I do too much with the config file in x11.

I did get the instuctions printed that you pointed me at and will read them and with a different PCI card I'll give it another shot.

Thanks,

Buttonpusher

---

