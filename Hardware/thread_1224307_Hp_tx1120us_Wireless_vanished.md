---
title: "Hp tx1120us Wireless vanished"
date: 2009-07-27
forum: Hardware
---

### Post by DigitalWolf333 on 2009-07-27
After first installing ubuntu on my laptop using the update manager and installing the drivers for my wireless card via the hardware installer. Suddenly all wireless options vanished! like i didn't even have the function! even though it was working before i started up my laptop again for the third time.
 
 
can anyone help me, i've tried many tutorials and none work, help!!!!
 
i've even tried ndiswrapper, 
 
this is one of the tutorials i tried
 
 
[[COLOR=#444444]http://ubuntuforums.org/showpost.php...&postcount=257[/COLOR]]("http://ubuntuforums.org/showpost.php...&postcount=257")
 
also the hardware driver is gone as well so i can't reinstall it or anything, so its like it doesn't even detect it anymore
------------------------
(later update)
 
Ok so i reinstalled ubuntu 9.04 and reinstalled the drivers in the hardware installation window. i restarted and my wirelesss was back again...
 
after that i restarted 3 times with out doing anything to my computer...no problems at all there...
 
but after installing software and adding files from my back up disks then starting up again the next day my wireless is gone again...
 
could it be something i installed? i'll post my synaptics instalation history later in case something caused this somehow...
 
is there some way i could activate it my self?

---

### Post by DigitalWolf333 on 2009-07-27
Yup its some program, i uninstalled everything that i had installed the day before and restarted, i got not change, but after i did a clean up with computer janitor, my wireless came back... 

but i doubted it would work so i don't remember exactly what was on there O_o

this is what synaptics says...

> Commit Log for Mon Jul 27 09:34:39 2009


Removed the following packages:
compizconfig-settings-manager
libxmmsclient-glib1
libxmmsclient4
python-xmmsclient
simdock
simple-ccsm
wine
wine-gecko
xmms2
xmms2-client-cli
xmms2-core
xmms2-plugin-alsa
xmms2-plugin-asf
xmms2-plugin-avcodec
xmms2-plugin-id3v2
xmms2-plugin-mad
xmms2-plugin-mp4
xmms2-plugin-vorbis
xmms2tray
but this seems like its only a list of what i had removed before the clean up...

it is more likely that the problem lies with the Compiz manager (and simple one) or wine since i had these two installed the last time i had this problem

---

### Post by DigitalWolf333 on 2009-07-27
ok it seems to be related to the compiz manager(python?), or it could be effected by synaptic altogether...

---

### Post by DigitalWolf333 on 2009-07-27
anyhelp at all?

---

### Post by DigitalWolf333 on 2009-07-28
oh crap, i think its a hardware or bios issue, turns out many tx1000 laptops have had the same problem, mine just occured now O_O
 
Everyones wireless goes in and out upon rebooting until it eventually stops all together!
 
and fixing it seems to be useless...

---

### Post by DigitalWolf333 on 2009-07-29
nope not a bios issue...
 
 
and it seems like no one has been able to get it fixed...
 
all the info i find is from 2008 anyway...(sigh) aw well... guess i'll just lve with it till i get a new laptop...

---

### Post by ZaHACKieL on 2009-07-29
Hey, have you tried with the new kernel?
Besides that, can you try the wifi in Windows or another OS?
Let me know

ZL

---

