---
title: "Hardware compatibility in a friend's Dell Inspiron E1505"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by ThinkBuntu on 2007-05-02
My girlfriend has a Dell Inspiron E1505 (laptop) and Windows is giving her problems, so I've encouraged her to give a Linux distro, namely Ubuntu, a try. The potential "problem" parts it has are:

Screen: 1680x1050-WSXGA
Graphics: Either Intel® Graphics Media Accelerator 950 or 128MB ATI Mobility Radeon X1300
Wirelss: Dell Wireless 1390b/g (54Mbps)

Will these work fine out-of-the-box, 3D effects not included (although those would be nice)? Most important is that resolution will work and that wireless will perform well. I could edit the xorg.conf file, but that would be a drag.

---

### Post by ph0neman on 2007-05-02
I got edgy 6.10 working with my wireless card using the ndiswrapper.  I also got beryl working nicely with the ATI 8.28 drivers and a little help from ENVY.  However, I have not had as much luck with Feisty Fawn 7.04.  I have loaded that twice on my laptop and am having video problems. 

Just thought I'd share my experiences.  Good Luck with your fresh install.

---

### Post by ThinkBuntu on 2007-05-02
In that case, you would recommend Linux Mint I'm guessing? It comes with an ndiswrapper frontend and Envy, and is based on Edgy. Quick questions:

1) How is ndiswrapper reception? Is it as good as if you were using Windows? I ask because the open source drivers running on my Atheros AR5212 get relatively poor reception. I bought my ThinkPad used, so I don't have access to the driver...

EDIT: Forget #2. Found it on the Dell support site.
2) Could you please email me the driver(s) you use, zipped? (assuming it's the same wireless card. If you're using an E1505, it is). I could send you a PM with one of my email addresses. The hopeful Ubuntu recipient is not the technically inclined type, so I doubt she knows where her driver(s) are.

---

### Post by Syke on 2007-05-02
> Graphics: Either Intel® Graphics Media Accelerator 950 or 128MB ATI Mobility Radeon X1300
Which one is it?

For Intel GMA 950, you'll probably just need to run the [915resolution fix]("http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html"). You should be able to get the nice 3D effects too.

---

### Post by ph0neman on 2007-05-03
> **ThinkBuntu said:**
> My girlfriend has a Dell Inspiron E1505 (laptop) and Windows is giving her problems, so I've encouraged her to give a Linux distro, namely Ubuntu, a try. The potential "problem" parts it has are:

Screen: 1680x1050-WSXGA
Graphics: Either Intel® Graphics Media Accelerator 950 or 128MB ATI Mobility Radeon X1300
Wirelss: Dell Wireless 1390b/g (54Mbps)

Will these work fine out-of-the-box, 3D effects not included (although those would be nice)? Most important is that resolution will work and that wireless will perform well. I could edit the xorg.conf file, but that would be a drag.

heya ThinkBuntu: I ended up using the R151517.exe from dell use the following command:

wget [http://ftp.us.dell.com/netowrk/R151517.EXE](http://ftp.us.dell.com/netowrk/R151517.EXE)

several options for you are to check the link here:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

or if you are goint to install Feisty Fawn 7.04 this site has a script that will configure your ATI x1300 plus your wireless and install beryl at the same time.  good luck let us know how it goes. 

[http://www.mylittleubuntuguide.com/category/how-to/](http://www.mylittleubuntuguide.com/category/how-to/)  

if you follow that to the T... it seems to work with minimal effort.  I was able to manually config my Edgy install but it was a pain in the *** this was easy as pie.  
**[COLOR="Red"] btw: the ndiswrapper seems to work alright I'm about 40 feet from my wireless connection and it works great. [/COLOR]**

---

