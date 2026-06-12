---
title: "ati mobility radeon HD 2400 XT in ubuntu Janty 9.04"
date: 2009-10-05
forum: Hardware
---

### Post by babik_ on 2009-10-05
I have an acer Travelmate 5520 with this graphics card in it. My problem is that i cant get it to function properly. I have installed the latest ati drivers for linux from ati's website but everything connected to the graphics seems to lag a whole lot. Compiz fusion and desktop graphics is very slow and laggy. I also tried to play some windows games through wine but they also lag a whole lot. I wish someone could help me get my graphics card working properly because i love everything else about ubuntu. :P

---

### Post by babik_ on 2009-10-05
anyone?

---

### Post by babik_ on 2009-10-05
really? noone?

---

### Post by Yellow Pasque on 2009-10-05
Make sure you installed the driver correctly: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by babik_ on 2009-10-07
Ok, neither of the guides worked for me. Isn't there anyone who has the same card who's got it working??

---

### Post by babik_ on 2009-10-10
please, i've tried everything! Isn't there someone out there who has solved the problem with this graphics card??? I would be so thankful if someone could help me!!!

---

### Post by @ntonius on 2009-10-17
I have the HD 2400Pro
The latest ati (fglrx) drivers work perfectly for me which you can find at the official ati-amd site.
Follow the instructions here [http://wiki.cchtml.com/](http://wiki.cchtml.com/)
and dont forget to remove the open source drivers "ati" and "radeon" from synaptic (which are pre installed by default).
I had flickering before removing the open "ati" and "radeon" drivers. For some reason this corrected the problem.

---

### Post by 2eagle2 on 2009-10-19
I also have the same model as you - ATI mobility radeon HD 2400 XT
all I can say you is that the compiz is slow, I also have some bugs (fo exemple same flash video on webs sudenly disappear etc.) I just hope that the new release of ATI fill fix it.
when I enable benchmark in Compiz I get max 60fps which is too low (in case that I dont do anything, during cube rotation I get about half of it 30fps) 
I will be more than happy if someone find a glue on it :)

---

### Post by 2eagle2 on 2009-10-26
I found that when I Installed an no-backfill xserver from ppa [https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)
it make compiz to run faster - much better reaction now I dont have to wait 1-2s to maximalize or resize window (when I installed it I get blank screen after reboot, but when I reinstal the fglr driver it work great! ) maybe it could be also useful for you. have a luck.

---

