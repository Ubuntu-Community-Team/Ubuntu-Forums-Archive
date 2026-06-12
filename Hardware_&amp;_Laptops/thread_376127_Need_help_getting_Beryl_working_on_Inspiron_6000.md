---
title: "Need help getting Beryl working on Inspiron 6000"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by JohnnyReb on 2007-03-04
I've tried several times with no luck. The laptop locks up after logging in. 

I assume this can be done as others have posted that they have it running but they didn't post how they did it. 

Video Card=ATI Radeon Mobility M300

Can someone please help? I'm sort of new to linux, so a step by step guide would be nice.


Thanks
David

---

### Post by JohnnyReb on 2007-03-04
maybe I should clarify a little, 

The system locks up after logging into an xgl session. I followed this tutorial

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

To the letter. Still not having much luck. I would really like to play with the 3D desktop.

Thanks
David

---

### Post by JohnnyReb on 2007-03-05
Anyone? I know I can't be the only one running Edgy on a Dell Inspiron 6000:confused:

---

### Post by dbott67 on 2007-03-05
I've got an Inspiron 6400 running Edgy & Beryl.  I've also done it on Dapper.

I've written up the steps that I took in getting everything working here:

[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

Good luck,
Dave

---

### Post by JohnnyReb on 2007-03-05
Thanks Dave, that was a huge help! I got a lot farther this time. Got an xgl session going played around with the cube and stuff, but unfortunately it's just not stable. Locks up or reboots after about 15 minutes or so. 

Take Care
David

---

### Post by dbott67 on 2007-03-05
No problem.  I've not updated my SVN packages for Beryl since I installed it (still running 0.2.0 RC1 from ~Feb. 12 or so).  I understand that a lot of people had troubles with later releases of Beryl with white cubes & crashing & what-not.

If you can find an older version of Beryl (I think 0.1.99.2 was recommended somewhere) you may have better luck.  Try checking [www.beryl-project.org](www.beryl-project.org) forums --- specifically this thread:

[http://forum.beryl-project.org/viewtopic.php?f=36&t=4046](http://forum.beryl-project.org/viewtopic.php?f=36&t=4046)

The thread is about 6 pages, but all of the postss have happened within the last 2 weeks.  It may get you going.

Keep in mind that you'll probably need to use Trevino's repository (if you're not already).

-Dave

---

### Post by SkyWasher on 2007-06-03
Hello 
I have an Inspiron 6000 I got Beryl on Feisty to work by un-checking the ATI restricted driver in System > Restricted Driver Manager. 

After going  through several tutorials  this is the only way that  I found to get it working.  I can't tell you why it just does..  Good luck!.  

I'd be curious if this worked with others..  Now if I could just get the wifi LED to work.. 

My xorg.conf file: 

```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

---

