---
title: "another ati question.."
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by oogie on 2005-09-12
alright you guys. Im very new to this linux thing. I have no prior knowledge of this OS other then what i found messing with it tonight. So far i really like it. 2 problems though. Well, a major problem is i have not enough training to actually figure stuff out.. but, i have an ATI 7200 dual monitor video card. Can anyone take a few minutes if they got some free time and write me a idiot proof walkthrew of it? ive been trying things all night an most of them dont work or are like, just do this with that and i have no idea what their saying. One off the topic question, i want to listen to Mp3's and beleive it or not, i couldnt get those how to's to work either.. please, help me alittle on this an maybe i can start picking up on it...

---

### Post by Bruce3000 on 2005-09-12
[QUOTE=oogie]alright you guys. Im very new to this linux thing. I have no prior knowledge of this OS other then what i found messing with it tonight. So far i really like it. 2 problems though. Well, a major problem is i have not enough training to actually figure stuff out.. but, i have an ATI 7200 dual monitor video card. Can anyone take a few minutes if they got some free time and write me a idiot proof walkthrew of it? ive been trying things all night an most of them dont work or are like, just do this with that and i have no idea what their saying. One off the topic question, i want to listen to Mp3's and beleive it or not, i couldnt get those how to's to work either.. please, help me alittle on this an maybe i can start picking up on it...[/QUOTE]

Okay... on the MP3s, give me a PM on that one, because MP3 is propriatary - ie to make an MP3 codec you have to fork out the $$$. I'll explain in further detail in PM why it is illegal(ish) - cough - - cough -

As for your video card... open up synaptic and search for "xorg-driver"... the one you are looking for should bee something like "xorg-driver-fglrx" - install that. The nwhen you have done that, pop up a terminal window (right click on desktop).

type glxgears and take note of the MPS. Close the pop-up window.

type sudo nano /etc/X11/xorg.conf

scroll down to the section "Device" and change:

Driver "*whatever it has here*"    to    Driver "*fglrx*"

also add the following line:

Option "UseInternalAGPGART" "no"

between the Driver and busID line...

Hit ctrl+x and say yes to writing changes...

Reboot your computer and log-in.

Open up another terminal windows and type glxgears... the MPS should be higher now...

As for dual-display; forget it lol. ;)

Hope this helps...

Cheers

Bruce

---

### Post by Granji on 2005-09-12
[QUOTE=oogie]alright you guys. Im very new to this linux thing. I have no prior knowledge of this OS other then what i found messing with it tonight. So far i really like it. 2 problems though. Well, a major problem is i have not enough training to actually figure stuff out.. but, i have an ATI 7200 dual monitor video card. Can anyone take a few minutes if they got some free time and write me a idiot proof walkthrew of it? ive been trying things all night an most of them dont work or are like, just do this with that and i have no idea what their saying. One off the topic question, i want to listen to Mp3's and beleive it or not, i couldnt get those how to's to work either.. please, help me alittle on this an maybe i can start picking up on it...[/QUOTE]

Okay, so I spent 2 days getting my Radeon 9550 to work, and With the help of mlomker, cause I give credit where credit is due, I did this

First, open synaptic, and do a search for fglrx, and get rid of the packages that are already installed, this will allow for a fresh installation of the proper drivers. Next, open a terminal window and follow these commands

[B]
su ( I personally use sudo -s -H ) 
apt-get install alien
alien -D fglrx_4_3_0-8.16.20-1.i386.rpm
dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh
[/B]

and if the module build succeeds, your drivers should be recognized on reboot, using the** fglrxinfo ** command from a terminal window.

If you get something back saying that MESA drivers are still being loaded, post the contents of your **xorg.conf** and your ** /etc/modules ** file please.

Hope this helps, it's the only way I could get my ATI card to work properly

---

### Post by [Koba] on 2005-09-12
I'm loath to do this but I am getting desperate.  :? 

I also have an X300 and having problems with ATI drivers. Forgive me for cross posting but my thread from earlier today seems to be sinking fast with no views!

[http://www.ubuntuforums.org/showthread.php?t=64987](http://www.ubuntuforums.org/showthread.php?t=64987)

In no way am I hijacking the thread (honest  ;-) ). Any solution here may come in useful to me too.

Thank you

[Koba]

---

### Post by mlomker on 2005-09-12
[QUOTE='[Koba]']I'm loath to do this but I am getting desperate.  :? 
[/QUOTE]

I'd recommend deleting everything related to fglrx on your machine and starting from scratch...it's the only reliable way.

[Here's the thread that Granji mentioned.](http://www.ubuntuforums.org/showthread.php?t=64286)

---

### Post by Bruce3000 on 2005-09-13
Good greif! I forgot to mention removing the old drivers! Perhaps I should audition for the part of Forgetful Jones on Sesame Street!

---

### Post by [Koba] on 2005-09-13
Hi

I tried that method using alien but my system was a mess when I used it so maybe it didn't work because of it. I've tried using this website ([http://www.objorkum.com/scripts/fglrxconfig/](http://www.objorkum.com/scripts/fglrxconfig/)) to generate my conf files, I've tried using the ATI installer for Xorg, I've tried making distribution specific packages, I've tried the wiki guide ([https://wiki.ubuntu.com/BinaryDriverHowto/ATI)](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)), I've tried deleting everything using 

su
updatedb
locate fglrx | more

And finally when one of my attempts complained about a shared object file related to the Mesa drivers in desperation I uninstalled Mesa from synaptic. Big mistake. So finally after managing to recover XWindows three or four times from my backup conf file...I need to reinstall ubuntu (Xwindows doesn't even try to start anymore).

Admittedly, using [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) I got a nice output from fglrxinfo and a frame rate of about 3000 on one of the gears demos. It looks like that was the most successful I have been so far so that is what I shall try next time...unless someone kindly suggests something otherwise.

I have promised myself I am not going to reinstall Windows until I get this working.

Thank you for your time,

koba

---

### Post by mlomker on 2005-09-14
[QUOTE='[Koba]']
Admittedly, using [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) I got a nice output from fglrxinfo and a frame rate of about 3000 on one of the gears demos. It looks like that was the most successful I have been so far so that is what I shall try next time...unless someone kindly suggests something otherwise.
[/QUOTE]

Yeah, removing MESA is bad.  I wrote my method up in a detailed [HOW-TO](http://www.ubuntuforums.org/showthread.php?p=348911).  If you take that approach then I'll give you a hand.  You'll notice that I talk about the MESA issue at the end of my post and how to deal with it.

---

