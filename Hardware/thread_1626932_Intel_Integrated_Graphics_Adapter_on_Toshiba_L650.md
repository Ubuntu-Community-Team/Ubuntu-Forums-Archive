---
title: "Intel Integrated Graphics Adapter on Toshiba L650"
date: 2010-11-20
forum: Hardware
---

### Post by harris.sw on 2010-11-20
I was given a new Toshiba Satellite L650 with an intel i5 processor that has and Integrated Graphics Adapter.  I am new to Ubuntu and am trying to get rid of Windows 7 and use Ubuntu 10.10  I can't get enhanced video to work (3d, compositing).  System-Administration-Additional Drivers does not show any graphics adapter.

Looking around forums it looks like I need to download intel specific drivers.  I got them from intellinuxgraphics.org and I downloaded the 2010Q2 drivers.  
Sudo ./confiugre works fine
Sudo make I get the following error on the end:

checking for XORG... configure: error: Package requirements (xorg-server >= 1.6 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

My questions:
1. Should getting this driver installed make they system work?
2. If so, what do I need to do to finish installing the driver.

Sorry but a newbie here and trying my best!

---

### Post by harris.sw on 2010-11-24
Any suggestions where else I can look to try and get this to work?

---

### Post by mikewhatever on 2010-11-24
Hey, don't really have the solution for you, just wanted to say that others report desktop effects working with Intel's i5.
[http://ubuntuforums.org/showthread.php?p=10147613#post10147613](http://ubuntuforums.org/showthread.php?p=10147613#post10147613)
That said, graphical performance is nowhere near  compared to Windows.

---

### Post by harris.sw on 2010-11-27
I would be happy being able to use compiz effects,  basic games, etc, that post refers to.  I am running 10.10 but the integrated graphics doesn't work.  I was hoping someone had experience installing the drivers from intellinuxgraphics.org but no luck.

---

### Post by deanjm1963 on 2010-11-27
The drivers that are installed by ubuntu are the same ones from intellinuxgraphics.org. They should be automatically installed. Are you able to look into your bios and determine how much ram is set aside for graphics? I have an i5 and I have no problems with compiz etc.

Also, there are no propriety graphics drivers for intel, they're all open-source, that's why there are no "additional drivers".

If you go to Preferences > Appearance > Visual Effects - what does it say?

---

### Post by harris.sw on 2010-11-27
I looked through the BIOS settings and on no tab or additional setting was I able to see a RAM setting for the graphics.  It's an I5 with an integrated graphics adapter.

When I try the appearance - visual effects its set to none.  When I set it to Extra a window pops up saying searching for drivers, then the appearance-visual effects window greys out, becomes unresponsive, can't close it.

Take it this isn't a good sign?

---

### Post by deanjm1963 on 2010-11-27
It's a strange one - I'm using the same graphics as you, intel HD built into my i5 and I have no problems.

Did that driver you downloaded and attempted to install make any changes to the system at all?

Did you apply any updates after you first installed 10.10?

---

### Post by Yellow Pasque on 2010-11-27
Latest graphics drivers can always be had from: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

