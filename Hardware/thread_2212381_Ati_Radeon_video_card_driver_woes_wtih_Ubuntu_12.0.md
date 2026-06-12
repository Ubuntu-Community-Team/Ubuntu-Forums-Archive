---
title: "Ati Radeon video card driver woes wtih Ubuntu 12.04"
date: 2014-03-20
forum: Hardware
---

### Post by Pete_Jorg on 2014-03-20
a

---

### Post by deadflowr on 2014-03-21
Good news and bad news.
Bad news, the 4000 series card can only use the default drivers.
AMD stop supporting that card some time ago.
The good news the 5000 series card is still supported and you can install the AMD driver for it.

No need to go to the website and get them. Install them from Ubuntu's repo system.
In fact, in most cases, it is preferred to install the ones from within Ubuntu, as Ubuntu devs work to insure that the drivers don't break when ever an update happens.
(Though breakage can occur.)
To install from Ubuntu repo system open the menu system and search for the program called "Additional Drivers".
It should open and when loaded will list several drivers.
Usually it will have one recommended, or tested.
Click it and select the activate button.
This should install the driver.

If problems occur look over this
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

I hope this makes sense.

---

### Post by Mark Phelps on 2014-03-21
> but after restart I got a blue screen with stripes, 

NOT good news.  My guess is that your problem is that your machine has Switchable Graphics, and unless you can disable the HD 4xxx graphics, no AMD driver install is going to work.

My first approach would be to go into your BIOS and see if you can disable the HD 4xxx graphics (on-board graphics).  IF you can do that, it's likely that your previous driver install will work OK.

---

### Post by Yellow Pasque on 2014-03-21
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

### Post by Pete_Jorg on 2014-03-21
hmmm..........I tried "additional drivers"......and had poor luck.  It brought up three suggestions, but all three were listed as "2d drivers".  I tried one anyway, and got the same blue screen problem after reboot. I don't think I have tried the second or third one yet, because they appeared to be duplicate listings, and because it takes so long to reinall Ubuntu in order to recover from a driver error.

---

### Post by Pete_Jorg on 2014-03-21
I will try to see if I can figure out how to open my bios, and see what my options are.......thanks for the suggestion

---

### Post by Pete_Jorg on 2014-03-21
Temujin, I followed your link, and saw it talked about "mesa-utils".  I opened my software center and searched for it, and installed it.  Now "system settings > details > graphics" shows the driver is "Gallium 0.4 on AMD RS880", and the experience is "standard".  It appears the driver is recognized at least, but I don't know if I have made any real progress towards the goal yet.

---

### Post by Pete_Jorg on 2014-03-21
Mark,

I was able to access the bios setup, but interestingly I did not find anything in there at all about the video cards.  That surprised me, because I expected to find it - but I made a thorough search and did not find one reference to video or graphics.  I suppose this means I am up a creek without a paddle, so to speak.

---

### Post by Pete_Jorg on 2014-03-21
Deadflowr,

After installing "mesa-utils", the "additional drivers" utility brings up this one option:

"ATI/AMD proprietary FGLRX graphics driver (**expermimental ** beta).

It says "This package provides 2D display drivers and hardware accelerated OpenGL".  I presume that this driver will not allow me to play 3d games, but my understanding of the differences between 2d drivers and 3d drivers is very incomplete.  I had assumed all drivers could display 3 demonsional envoironments - unless they mean a 3D "effect" like you see in the movie theaters.  I will try this driver again as a last resort after I have exhausted any other remedies - since I expect it to trash my system and force me to reinstall Ubuntu again.

Any other thoughts?

---

### Post by Pete_Jorg on 2014-03-21
Mark,

I found some discussion of switchable graphics on a HP Pavilion dv7 4060us (which is my laptop), and so I presume mine DOES have switchable graphics.  

The discussion:  [http://forums.guru3d.com/showthread.php?t=369429](http://forums.guru3d.com/showthread.php?t=369429)

I recall that it in Windows 7 it does switch to a "low power" graphics mode when on battery, but I had no idea that this involved two seperate video cards.  I presume that there is a Windows 7 app that allows me to control the switchable graphics, but I also assume that this will not have any effect when I boot under Unbuntu.  Any other thoughts?

---

### Post by Yellow Pasque on 2014-03-21
> **Pete_Jorg said:**
> It says "This package provides 2D display drivers and **hardware accelerated OpenGL**".  I presume that this driver will not allow me to play 3d games

OpenGL = 3D, however, the Ubuntu driver program probably shouldn't be offering to install this binary driver for you because it won't work with the integrated graphics. You should concentrate on fixing the open-source/default drivers. They should be able to play games.

---

### Post by Mark Phelps on 2014-03-21
> I presume that there is a Windows 7 app that allows me to control the switchable graphics

In general, NO.  

Switchable Graphics (also known as Hybrid Graphics) are designed such that the graphics processor usage is automatically switched based on what you are trying to do at the time.  When you change activities to doing something that demands higher performance graphics, the PC switches automatically to the higher performance graphics chipset.

I've avoided this in my PCs, so I don't have first-hand experience using these, but from what I've read, the majority of the solutions (of not ALL of the solutions) to this situation in Linux involves disabling one of the two video chipsets -- effectively, "disabling" the Switchable Graphics feature.

---

### Post by Pete_Jorg on 2014-03-21
Temujin,

Thanks for your comment.  Unfortunately, I don't have a clue how to fix the open-source/default drivers.  Remembering that I am a novice, is there anything you can suggest for me?  Thanks again.

---

### Post by Yellow Pasque on 2014-03-22
You have to figure out exactly what is wrong before you try to fix it. Try to start the problematic application(s) in a terminal and see if you can get a specific error message. Just saying that an application won't run doesn't give you or me a whole lot of information to work with...
> I attempted to run Phoenix Firestorm for Linux on my Ubuntu 12.04, but the program will not launch.

Ultimately, the resolution may involve running a more recent version of Ubuntu and/or using a PPA to update the driver, like:  [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)

---

