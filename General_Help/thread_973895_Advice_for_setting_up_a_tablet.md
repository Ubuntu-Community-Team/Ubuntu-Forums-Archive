---
title: "Advice for setting up a tablet"
date: 2008-11-07
forum: General Help
---

### Post by leg on 2008-11-07
I have just been given a [hp compaq tc 4400 ]("http://reviews.cnet.co.uk/laptops/0,39030093,49287252,00.htm")tablet pc by work. They also may be getting a [Motion LE 1700]("http://www.motioncomputing.co.uk/products/tablet_pc_le17.asp") which I will also get to play with. 

My question is how well can I set up tablet functionality with a Linux OS. Things like the pen drive, shifting the screen from A4 to portrait when tilted or by a switch (depending on the tablet). Is there a distro that is well suited to this kind of PC or is it just a case of finding the software and setting it all up correctly. 

We would also be interested in controlling presentation software from it as well, our business is education. So this also suggests that controlling a room of PCs from it may be useful.

I haven't looked that closely at edubuntu yet but my impression of it is that it is aimed at primary schools judging from some of the software I noticed (am I wrong here).  

In short which distro, what software and set up advice.

Thanks

---

### Post by leg on 2008-11-08
Ok 8.10 is installed on the tc4400 but unable to get the stylus working. Have followed instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=590747") and the [wacom site]("http://linuxwacom.sourceforge.net/index.php/main").

The problem seems to be something to do with how xorg.conf is set up. After adding the devices to xorg.conf the instructions state that I should add those devices to the "ServerLayout" section. Problem is that my file does not have this section. If I add it and add the devices to it I get a parsing error when I restart X. Where and how do I add the devices?

---

### Post by Borfo on 2009-01-07
Try this thread if you're still having trouble:
[http://ubuntuforums.org/showthread.php?t=767015](http://ubuntuforums.org/showthread.php?t=767015)

It's Hardy, not Intrepid, but it deals with tc4400's specifically.

---

### Post by Favux on 2009-01-07
Hi leg,

First you have to get the Linux Wacom Project's linuxwacom driver set up.  Check out Loic2's Wacom wiki's:

[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

[https://help.ubuntu.com/community/Wacom/LatestDriver]("https://help.ubuntu.com/community/Wacom/LatestDriver")

and associated threads. I just helped a couple folks get a TC4200 set up.  I don't know how different the hardware is but it may be worth a look:

[http://ubuntuforums.org/showthread.php?t=1027808]("http://ubuntuforums.org/showthread.php?t=1027808")

Another person, benner, I helped to set up is a teacher and he's looking into a wireless projector setup.  He might be worth contacting.

If you'd like to attach your xorg.conf as an attachment I can have a look at it.

---

