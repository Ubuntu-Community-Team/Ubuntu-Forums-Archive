---
title: "webcam howto anyone?"
date: 2005-11-21
forum: General Help
---

### Post by nikolai.m on 2005-11-21
i got logitech qiuckcam messenger. can anyone help me to hook it up with kopete (or any other more suted for this task) messenger?
thnx..

---

### Post by nikolai.m on 2005-11-21
i see nobody is willing to give up this information....so webcam is doomed!

---

### Post by alvonsius on 2005-11-21
Well, it just only 10 hours from your last post ... so be patient. Have you try asking Mr. Google ?? :D

---

### Post by nikolai.m on 2005-11-22
[QUOTE=alvonsius]Well, it just only 10 hours from your last post ... so be patient. Have you try asking Mr. Google ?? :D[/QUOTE]
of course....there are so many different and complicated ways...i'd ruther wait till some wizkid from kubuntu planet gives me clear explanation...

---

### Post by skyboy on 2005-11-22
mine is working pretty well on kopete. I can receive and send webcam without problems.
But only kopete from cvs or the one in KDE3.5rc1.
Install that first and see how it goes.

And dont get pissed of if people are not awake at the same time as you. A day = 24 hours !!

---

### Post by nikolai.m on 2005-11-22
[QUOTE=skyboy]
And dont get pissed of if people are not awake at the same time as you. A day = 24 hours !![/QUOTE]
i don't. it's just from my experience on this forum i usually get replies
within couple of hours. and besides...did i sound pissed off? i think you got me wrong here?....maybe disappointed, but certainly not pissed off...i'm not angry person, please don't portrate me as such.

---

### Post by patrick295767 on 2005-11-22
I just installed kopete now with the similar quickcam logitech.

-- I didnt managed to use the logitech .. .
I ll try another program ...

---

### Post by skyboy on 2005-11-23
did you install kopete CVS or kopete coming with KDE3.5rc1 ??

---

### Post by nikolai.m on 2005-11-23
[QUOTE=skyboy]did you install kopete CVS or kopete coming with KDE3.5rc1 ??[/QUOTE]
i got kopete that came preinstalled with Kbreezy...so my KDE is still 3.4. so i guess i got CVS.

---

### Post by skyboy on 2005-11-23
[QUOTE=nikolai.m]i got kopete that came preinstalled with Kbreezy...so my KDE is still 3.4. so i guess i got CVS.[/QUOTE]
That is why it doesn't have webcam support. Only the late CVS or the kopete released with KDE3.5rc1 have the webcam support.
Either install KDE3.5rc1 or download from CVS tree.

---

### Post by dresnu on 2005-12-01
I use kde 3.5 so I guess my kopete version is compatible with webcams. I have a logitech quickcam express (the one in american pie ;-) but I can't start a video conversation. When I try to send video on the msn network I get a blue screen and after a few seconds the window closes by it's self. Are there any settings I have to make in order to get my webcam working apart from just plugging it in?

---

### Post by jjmckay on 2005-12-02
All I can add is that Kopete detected my logitech Orbit without any special work at all.  I just upgraded kubuntu to KDE 3.5.   The only difference between WinXP and kubuntu now is that the preview webcam window updates a LOT slower in kubuntu.  I'm having a difficult time trying to find anything to speed the updates up because I know it can do 15fps at least and 30 at some lower resolutions.  Right now I'm getting about 1 fps, but I haven't done an actual webcam conversation yet.

edit: clicking "settings" then "Configure" shows this preview screen to select webcam, with preview video.

---

### Post by Chris_(medico_2001) on 2005-12-02
You could install camstream, just to check if your webcam is working:

sudo apt-get install camstream

---

### Post by hugelmopf on 2005-12-02
WRONG>>Try to "modprobe quickcam" and see, if your camera is found then.<<WRONG

I have not tried with Kopete yet , but this driver will provide you with a /dev/video0 device and I suppose that is, what Kopete uses.

EDIT: Sorry, I am wrong. This driver does not seem to work with the Quickcam Messenger. You will need to compile this one: [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

---

### Post by arnieboy on 2005-12-10
use the following howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

