---
title: "Has anyone successfully gotten a Radeon 320m card to work?"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Anthem on 2006-10-29
I have a laptop that I like except for the horrid graphics card, which I hate.  The card has never been well-supported, either by the open-source drivers or by the frglx driver.  Can anyone say whether the support is any better in Edgy?

EDIT:  The card is the Radeon 320m, also called the Mobility U1.

---

### Post by Anthem on 2006-10-30
Holy cow.  Left alone for one day, and it ends up on page 11.  That's a lot of traffic right there.

Hope it's not rude of me to bump it up a bit.

---

### Post by jetpeach on 2006-11-01
I have the same card and have tried in the past, but without much luck.  ATI's newer drivers, I've heard, don't work with our card.

I'm hoping it's better in Edgy as well.  The best thread I can find is very old on this though
[http://www.ubuntuforums.org/showthread.php?t=62517](http://www.ubuntuforums.org/showthread.php?t=62517)
oh and another thread here, but I see you've commented on that one already :)
[http://ubuntuforums.org/showthread.php?t=227860&highlight=320m](http://ubuntuforums.org/showthread.php?t=227860&highlight=320m)

do post if you're able to get this working, people definitely have been able to get it but unfortunately i'm not one of them...

oh here's on you may not have seen at linuxforums
[http://www.linuxquestions.org/questions/showthread.php?t=494912&highlight=320m](http://www.linuxquestions.org/questions/showthread.php?t=494912&highlight=320m)
the reply seemed to have tried quite a bit

---

### Post by Anthem on 2006-11-09
> **jetpeach said:**
> I'm hoping it's better in Edgy as well.  The best thread I can find is very old on this though
[http://www.ubuntuforums.org/showthread.php?t=62517](http://www.ubuntuforums.org/showthread.php?t=62517)

Hmm... that does look promising.  I'll give it a try and report back.

---

### Post by stephanz on 2006-11-09
I am new to Ubuntu (I installed 6.10 yesterday). Before Ubuntu I was using FC 2 or 3 (I can't remember). The IGP320m graphics processor worked fine in FC with X6R8.1. 
I didn't test yet if 3D acceleration works in Ubuntu 6.10 out of the box. 
I was trying to get the vga output of my laptop to work in order to use an additional TFT screen and expand the desktop to the second screen however I didn't have any success yet. I didn't try dual head under FC neither. 
Does anybody have any success with dual head on the IGP320M?
Regards
Stephan

---

### Post by stephanz on 2006-11-09
Can anyone tell me how I can check if 3d hardware acceleration works?
I tried all the 3d screen savers and they seem to use hardware acceleration. The frame rate seems pretty high... but I am not 100% certain that it is hardware accelerated...
regards
stephan

---

### Post by jetpeach on 2006-11-09
the easiest way to check how/if 3d is working is by typing, in the terminal,
glxgears
wait about 5-10 seconds without moving the mouse to much and in the terminal behind the gears it will print your frames per second.  my results is a crummy 249fps, which is not close to what it could be... i think with this card and the ideal driver setup we could have over 1000.
glxgears isn't a "real" benchmark (if you resize it the fps changes) but it gives a very simple measure of what is working.
if you get an error after typing glxgears, then you don't have glx enabled, meaning your performance is very bad (probably using using mesa, the something equivalent of the defaults in windows before installing video drivers there).

any word anthem on how things are working? i don't have time to fiddle, what a sad card this is, so much more potential but can't get it because of stupid drivers...

---

### Post by Anthem on 2006-11-09
I'm going to work on it tonight.  Right now, I get 270 fps.

EDIT:  Nope, I can't figure out where to unpack the files from freedesktop.

---

### Post by edemark on 2006-11-09
have a look on this post it worked for me. I have radeon igp 345m and i am runing dapper. Before followinfg this guide i had some 300 fps after i get 1100 in 24 bits color depth and 1600 in 16 bits color depth
[http://www.ubuntuforums.org/showthread.php?t=221672&highlight=7000VE](http://www.ubuntuforums.org/showthread.php?t=221672&highlight=7000VE)

good luck

---

### Post by stephanz on 2006-11-13
I followed the instructions given in the link above except the installation of the latest radeon driver since I am using edgy eft which comes with X.Org 7.1. Before that I got 250 fps and now I get 680. Does anyone have a higher performance?
Regards
Stephan

---

### Post by jetpeach on 2006-11-13
wow, i just followed the instructions in that thread and am now getting around 720 FPS!  maybe this isn't fantastic, but this is definitely the best i've ever gotten.

basically, here's a recap of the instructions, modified for using edgy:

first run in the terminal
```

sudo apt-get install linux-headers-generic make gcc driconf xserver-xorg-driver-radeon

```
you may wish to use aptitude (my preference, it's smarter but still a pain sometimes) instead of apt-get

From here it picks up from the thread (we don't have to install the radeon drivers as described in the thread, they're in edgy and were installed above, probably already).  i attached my xorg.conf for your reference, just in case you have problems though.  also, he doesn't mention changed the busID, which for me is different.  to find which busID to use type 
lspci | grep VGA
(case matters for VGA of course).  the numbers you see after this command are for your bus id (for me, 01:05.0 so 1:5:0 in the xorg.conf). 

so the rest is very straight-forward.  Let us know here if the above works for you, Anthem this may improve it for you as well!

quoted from the thread,

sudo gedit /etc/X11/xorg.conf and change the Device section to look like the following:

Section "Device"
	Identifier	"Radeon"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "true"
	Option	        "EnablePageFlip" "True"
	Option	        "UseInternalAGPGART" "no"
	Option	        "backingstore" "true"
	Option	        "AllowGLXWithComposite" "true"
	Option          "RenderAccel" "true"
EndSection

Ensure that you use the same identifier in the screen section if you change it in this section, leave it be is probably best.

Now run driconf. Do not run this as sudo, some user space applications will not pickup the changes if you do. In my case google earth would not run properly until I ran it as a regular user. (had to sudo rm .drirc before running as a regular user after I had run it as root.)

Change the TCL mode to "Use Software TCL Pipeline" and Use HyperZ to Yes. Save and quit.

Reboot [or just restart x by logging off and hitting control-alt-backspace] and run glxgears -printfps.

---

### Post by edemark on 2006-11-13
stephanz 

I guess that you can have a bit more of fps lowering the color depth from 24 to 16 bits in the xorg.conf. this gave me a boost of almost 50% more from 1100 to 1600 fps.
hope it helps

---

### Post by Trefenwyd on 2006-11-25
Using an IGP 320M, and some FPS tweaks, i was able to get beryl to work successfully, and get my FPS from ~255 to ~680.

this is also changing my default depth to 16 from 24.

---

