---
title: "ATI Mobility Radeon HD2600"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by DPic on 2008-02-09
I'm thinking of purchasing the Lenovo IdeaPad Y710 notebook which has the ATI Mobility Radeon HD2600 and i wanted to make sure that it is supported and would work with Ubuntu. 

I also wanted to make sure everything else was compatible which i believe it is but if anyone knows otherwise please let me know. 

thanks!

---

### Post by riesenpixel on 2008-02-09
Hello,

you will have to install the driver from ati.com
I've found a tutorial (in German, because I'm German) here:
[http://wiki.ubuntuusers.de/ATI-Grafikkarten/fglrx/Manuelle_Treiberinstallation](http://wiki.ubuntuusers.de/ATI-Grafikkarten/fglrx/Manuelle_Treiberinstallation)
If you don't find it elsewhere in English and if you want I will translate it into English.

Greetings

---

### Post by Warmask on 2008-03-18
People are having lots of problems with this HD 2600.  I would stay away from it, if you are planning on using Ubunut

---

### Post by Yellow Pasque on 2008-03-19
The open-source radeonhd driver is included in the new Hardy alpha release and can easily be installed in current Gutsy-based distros (see link in my sig). That will at least get you 2D support.

If you're interested in 3D acceleration, the Catalyst drivers are getting much better.

---

### Post by mc-red on 2008-03-26
Timujin,
Thanks for the link i'll check it out.
I was feeling good an hour or so ago having installed ubuntu but was starting to have misgivings with the comments on this hd2600 card.
Hopefully it will work ultimately.

p.s. i guess you're a civ III,iv fan.

---

### Post by Yellow Pasque on 2008-03-26
> **mc-red said:**
> p.s. i guess you're a civ III,iv fan.

Actually, I'm a student of history. It kind of saddens me to see people whose view of reality is so distorted by technology that they would assume I took the handle from a game instead of real life. (I have been guilty of similar things too, so don't mistake the previous sentence for condescension).

FWIW, I use the name because it roughly translates to 'Ironworker', which is similar to what my last name means in German. Anyway.....

If you're just doing an Ubuntu install now and you have very current hardware, I would recommend wiping out that install and using the 8.04 beta. I test drove the Kubuntu Beta LiveCD and was very impressed. I had no problems with video because the radeonhd drivers are built-in on the LiveCD whereas I constantly struggled with video on the Feisty and Gutsy CD's.

---

### Post by kobyashi on 2008-04-03
Try this
If fglrxinfo doesn't display the ATI name which I dont think it will (maybe something else like mesa) go here [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide).
This is a good walkthrough on how to add to 8.04 but there will be one for early versions.

If it does show Ati just try adding Option "TexturedVideo" under driver = fglrx in your xorg.conf. If it doesn't work I recommend the link.

Made enormous difference. I can now display 1920x1080 with MythTv whereas before it was very jerky.

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "TexturedVideo"
EndSection

---

### Post by EyePeaSea on 2008-04-03
> **DPic said:**
> I'm thinking of purchasing the Lenovo IdeaPad Y710 notebook which has the ATI Mobility Radeon HD2600 and i wanted to make sure that it is supported and would work with Ubuntu.!

The other people in this thread know a lot more about this stuff than I do - but my 2p worth is...

The simple answer is that Ubuntu 7.10 does work with the HD2600 (on my Compaq 8510p laptop), but it looks as if the drivers are limited; so no high res (I'm stuck on 1280x1024) and no 3d support.  However, the display is crisp and fast - no jerkiness.

If you only need this level of screen resolution and don't need 3d, then the current Ubuntu will work fine.

If you want full ATI support, then I guess you need to either wait for Ubuntu 8, or follow the suggestions in the rest of the thread (which is what I'll be doing - I have an irrational desire to get the most of the gfx card :) )

Regards


Ian

---

### Post by dynamethod on 2008-04-04
I bought a HD 2600 XT PCI-E Gigabyte Radeon card today, and man have i had trouble installing and getting such things as compiz to work, i had much much better luck with my previous X800 XT AGP card :S

---

### Post by sripplinger on 2008-04-10
I have the mobility radeon hd2600, too.  It seems like it was working (eventually) after my first install of Gutsy, but I reinstalled for different reasons and was then having issues with video flicker.  I had used Envy to install the ATI driver.  So, I decided to start from scratch, attempting some of the methods I've seen in the forums.  Nothing has worked yet.  In fact, when I now use Envy to install the driver I can't even get to the login screen.  I don't get it.

I'm hoping that Ubuntu 8.04 solves these issues.  I figure I can wait a couple of weeks for the official release.  In the meantime I'll just keep banging my head against Gutsy, hoping it will work well enough for me to survive until Hardy.

---

### Post by Yellow Pasque on 2008-04-10
> **sripplinger said:**
> I have the mobility radeon hd2600, too.  It seems like it was working (eventually) after my first install of Gutsy, but I reinstalled for different reasons and was then having issues with video flicker.  I had used Envy to install the ATI driver.  So, I decided to start from scratch, attempting some of the methods I've seen in the forums.  Nothing has worked yet.  In fact, when I now use Envy to install the driver I can't even get to the login screen.  I don't get it.

I'm hoping that Ubuntu 8.04 solves these issues.  I figure I can wait a couple of weeks for the official release.  In the meantime I'll just keep banging my head against Gutsy, hoping it will work well enough for me to survive until Hardy.
Use the open-source radeonhd driver (see link in my sig). It won't do 3D accel or desktop effects, but the 2D stuff is solid.

---

### Post by Caboose447 on 2008-04-26
I have a Toshiba Satellite A200-TH7, and it has a Mobility Radeon HD 2600. After installing the final build of Ubuntu 8.04, I found that in the restricted drivers, it was using an ATI Fire GL driver, which was enabled but not in use. Removing the checkmark, rebooting the notebook, then enabling the Restricted ATI Drivers and one more reboot worked. However, the flickering video I've found seems to have to do with a VSYNC issue with notebooks due to power limiting. One article suggested setting anti-aliasing and Anisotropic filtering to max (You can install the Catalyst Control Centre via Add/Remove Programs), I haven't tried that yet, but I will give it a go this afternoon. That might help.

---

### Post by Rekijitsu on 2008-05-07
Hi guys, sorry to bring up an age old topic...

I have tried Ubuntu twice, I love it to death, but I can't get 3D acceleration to work on a Toshiba Lifebook with Mobility HD 2600...

Way I understand it, is it takes a lot more effort to make laptop drivers because of their built-in monitors.

If someone could direct me to something that got the Mobility HD 2600 to have 3D graphics acceleration, I would be an Ubuntu convert completely. Sadly this laptop is my only one (college student) and if I can't game, I have to stick with good ole' Windows. If someone could direct me to a good link for getting 3D to work with Mobility HD 2600s, then I would be happy.

I tried Envy in the past, it gave me a driver that allowed me to have the fancier desktop environments (not compiz, but the 2D environments), but not run games. If you want to make a man happy with finally being able to be an Open Source conversion, please direct me to a Mobility link, that would be great.

---

### Post by Jorin on 2008-06-14
I have a Toshiba laptop with the Mobility Radeon HD2600, and I did get some kind of 3D acceleration working with Envy... The weird thing is that the restricted drivers are still not "in use" despite being "enabled." When I try to put them in use I get a black screen on startup and need to use xfix to get past that -which again disables the restricted drivers.

Even so, I can get the desktop cube and other effects just fine, but movie playback is pixelated and unsmoothed in full screen mode. Every resource I've checked on this matter just says "your drivers aren't configured properly." Well duh.

Basically I've given up on getting video to work correctly in Ubuntu on this laptop. I've read a lot of threads about this and there are no solutions that will get video working normally despite a lot of hard work. It's pretty sad because I want to convert to Ubuntu, but I can't do it if video playback and dual monitor support doesn't work.

---

### Post by Yellow Pasque on 2008-06-14
Jorin, try the radeonHD install guide (link in my sig). I'm going out right now, but I'll be back in a few hours if you have any questions.

---

### Post by sophie27 on 2008-06-26
Hi!
I have ATI Mobility Radeon HD 3470 on Kubuntu Hardy 8.04.
I've had some problems in configuring my monitor (1280x800)....

Now, I'm using a driver **fglrx** (downloaded here: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)) and the screen is quite ok. 
But I've not tried it in "movement" (movies or games)...

I've tried a driver **radeonhd**, but I don't know why, my monitor...fades out with it!!

I don't know which should be the best driver..........

---

