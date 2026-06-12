---
title: "Display Problem &quot;Intel HD Graphics&quot; on &quot;Acer Aspire 5742Z&quot;"
date: 2010-11-10
forum: Hardware
---

### Post by dea_jul on 2010-11-10
Hi guys,

I'm having trouble getting a new laptop to display after installing Ubuntu 10.10. On bootup, X fails to start and I get a login prompt. A minute after logging in, X starts with very low-resolution. This happens on its own regardless of what I'm doing or what commands I've issued.

Prior to setting up a default /etc/X11/xorg.conf config file (copied from xorg.conf.failsafe), I would get the same behavior, but X would instead *attempt* to start and fail, and I'd be left with a broken black screen until I rebooted. This failsafe config is using the vesa driver.

I've attached a package containing: 
* output from lspci
* Xorg.0.log file generated on bootup 
* Xorg.0.log.old file generated when I issued Xorg -configure 
* xorg.conf - the xorg.conf.failsafe file I'm using.

I've searched extensively for a working xorg.conf file for the Asus Aspire, or for "Intel HD Graphics", but haven't found one. I'm honestly not sure what driver to use, or even what the problem is. Any help, or pointers to a place I could find some useful information would be fantastic. 

Thanks!

---

### Post by vs8 on 2010-11-17
I have exactly the same issue with the same computer. 

What makes it even worse is the fact that the live session works perfectly (video wise), I even got Compiz running. The sound card is not recognised, suspend/resume and hibernate don't work either.

I've tried a live session of Natty Narwhal pre-alpha and everything works except hibernate and screen backlight control.

I used Checkbox to test the machine, when I installed it I got the same error, but the worse part is that safe graphics mode doesn't work at all.

---

### Post by vs8 on 2010-11-17
I have submitted a bug report, please mark "it affects me too".


Thank's in advance!

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/676805](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/676805)

---

### Post by vs8 on 2010-11-18
It started working properly after an update. I used Ubuntu Tweak added some PPAs and some apps, updated the system and now everything works as usual.

---

### Post by hollerith on 2010-11-20
Sorry, could you be a bit more specific please with the actions?  I just bought one of these laptops.  Would you link to the .iso you used and explain which packages and what you did etc?  At the moment, it boots slowly (I heard the ubuntu 'Aaaawwwwww!'), off an install usbkey I have.  But I can't see a thing.  Any assistance at all would be greatly appreciated, gratefully received.  Othewise its game face at ...

---

### Post by vs8 on 2010-11-20
Ok I can't be very specific about it because I wasn't expecting it to work I just added the PPAs I always use from Ubuntu Tweak.

X Updates and Gnome3 stack could be the ones that fixed it but I'm not sure since I tried X updates and X fresh Crack in two different installs and got the same text based login.

There was another guy who fixed the problem by simply downloading Linux 2.6.37 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/)

You can find the other thread here:

[http://ubuntuforums.org/showthread.php?p=10139361&posted=1#post10139361](http://ubuntuforums.org/showthread.php?p=10139361&posted=1#post10139361)

---

### Post by hollerith on 2010-11-21
Yeh, thanks for the reply. I know sometimes you just try things.  The thing is I'd be happy with some graphics at all.  

I don't know how you guys got Ubuntu (on the exact same model) because I burned the maverick iso to a usb key.  

When it boots I get -

Unknown keyword in configuration file
boot:

An older livecd/key gets to the try/install screen and boots from there except that I have absolutely no graphics from there on.  

What installer did you guys use?  

"I have a bad feeling about this".

---

### Post by vs8 on 2010-11-21
> **hollerith said:**
> Yeh, thanks for the reply. I know sometimes you just try things.  The thing is I'd be happy with some graphics at all.  

I don't know how you guys got Ubuntu (on the exact same model) because I burned the maverick iso to a usb key.  

When it boots I get -

Unknown keyword in configuration file
boot:

An older livecd/key gets to the try/install screen and boots from there except that I have absolutely no graphics from there on.  

What installer did you guys use?

I installed it via USB. When you get that message type "help" and hit enter. You should see the Ubuntu welcome screen in a few seconds.

It seems that the usb creator you used was buggy or the .iso has a problem.

You can also try using recovery mode on the installed system and run on safe graphics mode when you see the recovery prompt. If you get graphics install the latest kernel from the link a few posts above.

---

### Post by shram43 on 2010-12-18
Hi, guys. I have the same problem with Aspire 5742. But graphic system don't load even in low defination. 
Can you help me with kernel install from command line?

---

### Post by shram43 on 2010-12-22
thank's everyone for the help ;)
I solved the problem in this way:
```
sudo apt-get install linux-image-2.6.35-24
```

---

### Post by vs8 on 2011-03-06
Natty can't control the backlight as with Maverick. I thought it would get fixed with Linux 2.6.38.

---

### Post by inkrypted on 2011-03-06
The best solution for the video problem is the X-Swat PPA which is ppa:ubuntu-x-swat/x-updates 
Which will get you the latest video driver and the headers you need.

---

### Post by vs8 on 2011-03-06
I've tried this on Maverick, I always add the X updates PPA via Ubuntu Tweak but it still doesn't work. I will try it on Natty and post the results.

---

### Post by vs8 on 2011-03-06
Nothing new, Natty seems to have the latest and greatest drivers and headers.

---

