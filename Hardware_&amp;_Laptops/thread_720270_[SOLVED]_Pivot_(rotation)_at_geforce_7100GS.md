---
title: "[SOLVED] Pivot (rotation) at geforce 7100GS"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by swotie on 2008-03-10
The Pivot function will not work at my Geforce 71100GS .... I can see the function (rotation) under options, but it is inactive ... hwat can I do to activate this function 

Hope somebody can help me ... I miss my pivot

---

### Post by oldsoundguy on 2008-03-10
this worked for me on three Gutsy installs using NVidia cards:

First .. I used ENVY (a third party program) to install the drivers.

Then, to activate the rotate button:  Open terminal under Application> Adminstration
Type in:    sudo nano /etc/X11/xorg.conf     (**note the X is upper case**)  hit enter
enter your password
(nano (an editor) will open and have the xorg.conf file ready for you to edit.)
scroll down to the NVida card entry.
below the driver line type in (THE WHOLE LINE):
Option        "RandRRotation"     "on"    (**note again the upper case letters**)(emulate the line above your entry)
hit control o
hit enter (this will re-write xorg conf file and create a back up of the old file)
hit control x (this will exit)
then control/alternate/backspace
sign in again
go to >System> preferences> resolution
the rotation choice should now be usable.

---

### Post by swotie on 2008-03-10
It will not work for me :-( ... maybe i'm a Dummy :-|

---

### Post by oldsoundguy on 2008-03-10
try removing your video drivers and re-installing using ENVY:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Then do the code work.

---

### Post by swotie on 2008-03-11
I have installed ENVY ... removed old driver ... installed new driver automatic  ... rebooted my computer .... It don't work for me

---

### Post by oldsoundguy on 2008-03-11
after you re-booted, did you go into terminal and do as I showed?  UNLESS you do that, you are right, it will not work.  It will not pivot by default.  It (xorg.conf) has to be told that that option is available.

---

### Post by swotie on 2008-03-11
He He ... it works now .... THANK YOU very much ...

---

### Post by swotie on 2008-03-12
a little problem more ... when I reboot, the settings I have made, has gone .... Then I must set the rotation settings again

---

### Post by oldsoundguy on 2008-03-12
you shouldn't have to edit anything .. just go to the resolution control and flip it as you found ... for some reason it does not remember the position when you shut down or re-boot ..... annoying, but something you CAN live with until a patch is written or someone comes out with some added code we can plug in.
All my machines are that way at present.  But I so seldom re-boot, that it has not been a major issue.  My machines are on 24/7 running BOINC from UC Berkeley.

You could go the the NVida Linux forum and ask there .. I did and got a lot of the same responses I posted here .. "yea, that's the way it is" comments, but NO solution YET!

---

### Post by dark_phantom on 2008-03-12
I will have to try this, thanks for those steps.

---

