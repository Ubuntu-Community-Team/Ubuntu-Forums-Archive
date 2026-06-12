---
title: "XServer fails to start with 7.04 CD on Dell 6400/E1505"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by Mr_Congeniality on 2007-05-22
I can't even get into Ubuntu to set it up on my laptop.  It says caught signal 11 or something and aborts the installation when I try to do dpkg-reconfigure xserver-xorg.  I set it all up correctly like I had on my previous installations, except this being a live CD.

What the hell do I do?

---

### Post by ipatec on 2007-05-22
I'm having the same problem on a Dell 6400/E1505, but I've installed UbuntuStudio 7.04, any advice?

---

### Post by Mr_Congeniality on 2007-05-22
Come on there's got to be something.

I'm using a the CD shipped to me and I can't get the OS to boot to install it.

---

### Post by fejimush on 2007-05-24
You can add another one to this list. 

I am pretty certain it is related to the ATI graphics card (in my case ATI x1400).

Has anyone been able to load Ubuntu 7.04 on a Dell E1505 laptop?

thanks,
fej

---

### Post by myoungf1 on 2007-05-24
If you are having problems with the live cd coming up then you might try to use the alternate cd instead.  It has a text line installer that works very well.

---

### Post by init6 on 2007-05-24
I've ran the alternate install of ubuntu studio on my dell xps and it installs fine.  However, the xserver will not start.  

I've ran the alternate install of ubuntu studio on my desktop and it installs find.  However, ati drivers won't install and I can't get direct rendering enabled.

Both are using ati graphics cards.  I've read the xorg 7.2 is the culprit, but I cannot prove it.   

I'm interested in an answer to this myself.

---

### Post by myoungf1 on 2007-05-24
The proprietary ATI drivers are not built for the Xorg 7.2 thus getting them to work is a real chore to do.  Here is a link to a how to to get the ATI proprietary drivers installed on Feisty.  This should help but getting direct rendering will be a roll of the dice as some people get it working and others don't.  You could use the open source ati drivers, I don't know what they are called, but they are not nearly as good as the proprietary ati drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by init6 on 2007-05-27
dpkg-reconfigure xserver-xorg fixed my laptop woes.   Even 3d was enabled without any more hacking.  Still have issues with my desktop though.

---

