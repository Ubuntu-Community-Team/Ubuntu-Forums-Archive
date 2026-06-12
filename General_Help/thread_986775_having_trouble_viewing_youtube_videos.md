---
title: "having trouble viewing youtube videos"
date: 2008-11-18
forum: General Help
---

### Post by Gatorade on 2008-11-18
I'm trying to install flash so I can view youtube videos but I'm having trouble getting it to work .


any help would be appreciated, I'm a newby to linux so go slow.



thanks.

---

### Post by jackashe on 2008-11-18
what browser are you using? what kind of trouble are you running into? crashed the browser; says flash not installed..?

---

### Post by easoukenka on 2008-11-19
without more details here is what i recommend

right click where flash should be what version does it say?  

Download flash from adobe's site preferably version 10 and extract those files

Extract those files to a folder on your desktop

close firefox

now open the terminal

type locate libflashplayer.so

then type sudo rm (enter all pathes listed in locate eg rm /home/eric/.mozilla/plugins/libflash.so /usr/bin/firefox/plugins/libflashplayer.so etc)

now type cd ~/Desktop/(folder you extracted files to)

type ls

sudo chmod +x (name of the flash installer)

./(name of the flash installer)  

It will walk you through the rest and now you have version 10

---

### Post by mcheshpants on 2008-11-19
try to install flash player through synaptic package manager instead of the adobe website

---

### Post by Gatorade on 2008-11-19
thanks for the suggestions. after trying a ton of different stuff its finally working.

I'm not exactly sure what fixed it , but I really can't complain.

I would've liked to know what it was that did the trick just for future reference but for now I'll be happy.

---

### Post by volaer on 2008-11-19
I don't know exactly if this really will help... sometimes, when you are running an installation especially if it concerns your browser, you have to close your browser after the installation and open it again before the installation will take effect. 

The same thing if it is a computer program, once installed, your pc needs to reboot. There should be no problem upon installation automatic installation... of course, it will not really work until you close your current browser then open it up again... there the change will take effect. 
:)

---

### Post by Gatorade on 2008-11-19
that's a possibility.

I did try that before and had no luck. but when I did another restart maybe then they finally went into effect.

here's a solution I was given by another member that worked

[http://ubuntuforums.org/showthread.php?t=1308512]("http://ubuntuforums.org/showthread.php?t=1308512")

---

