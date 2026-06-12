---
title: "Inspiron 1501: Couple of things still not working."
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by hades_6_6_6 on 2006-11-22
Thank to [this thread]("http://ubuntuforums.org/showthread.php?t=299929") I was able to install Edgy and configure wifi properly. But still there are a couple of things I couldn't manage to configure. Maybe can somebody help on one or the other issue.
[LIST]
[*]**Standby not working**
Standby is "working fine", but there is no way to wake up. I have to to hold the power button for 10 seconds - or remove the battery - in order to use the system again. 
[*]**Hibernation not working**
The system crashes while trying to go into hibernation mode, saying a device is consuming too much.
[*]**Beryl not working**
I tried to install Beryl following [this method]("http://ubuntuforums.org/showthread.php?t=265678") (Radeon open source driver, aiglx, and Beryl). Installation was easy but when I start the beryl-manager, the Beryl splash screen appears for a couple of seconds and then the X-Server restarts.
[/LIST]

---

### Post by hades_6_6_6 on 2006-11-29
I still couldn't solve any of the problems above.
Does somebody has a solution (at least for one of the issues)?

---

### Post by mues on 2006-11-29
Hmmm... why beryl?
The ATI driver 8.29.6 for linux does its job very well:
[http://www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.29.6.run](http://www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.29.6.run)

Greets,
- mues

---

### Post by redDEADresolve on 2006-11-30
the ati open source driver doesn't work for any cards above x800. The cards in the dell fall into that category. Try setting up the new ati driver X1000 cards and up. 

Use This:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Then Setup an XGL session:
[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL)

That should solve your Beryl Problems

---

### Post by jlapier on 2006-12-06
I haven't tried Beryl yet but I have got the ATI proprietary drivers working (NWN works pretty good). I'll try beryl maybe this weekend or something - personally when I get into developer mode and I want to start swapping workspaces, that 3D crap makes me dizzy and I usually switch out of gnome into wmii anyway. My only interest in beryl would be to taunt Mac users (oh, your $2000+ laptop is so pretty - well, big deal my $599 laptop looks just as good...)

Anyway, my only problems with my 1501, running Edgy AMD-64:

(1) No hibernation or suspend mode sucks - I hate having to shut it down and restart all the time 
(2) The ATI drivers work fine, but they only use the 128MB of video ram - you're supposed to be able to use up to 128MB of system ram for a total of 256MB for video - I think the Dell e1505's let you configure this in the BIOS, but I can't find any way to do this in my BIOS and I suspect it's because the 'doze drivers let you configure it in the driver settings somewhere. Anyone know how to do this for the 1501?
(3) Wifi works...but...not on startup. I have to open the Gnome Network Admin applet after the desktop loads and then open the configuration page for my wlan card, uncheck "Enable this connection", recheck it, and that forces the wlan card to wake up and connect to my home network. My network is password protected, I don't know if that has anything to do with it.

All in all, things work pretty good and I'm very happy with it. If I could find fixes for these three issues, I'd declare it the best $599 I've spent in quite some time :)

- Jason

---

### Post by flyguy101 on 2006-12-06
I am having problems with this laptop to i been trying to fix for about 3 days....I am having a problem trying to connect to the internet... Even when i plug in the Ethernet cord it say i am sending out packages but not recieving any...and it is not working....
I have also tried to connect it to my router using the wireless connection and that wont connect either for some reason....I put in the WEP or whatever......and when i hit connect nothing happens do anyone know a answer to this....

---

### Post by redDEADresolve on 2007-01-09
> **flyguy101 said:**
> I am having problems with this laptop to i been trying to fix for about 3 days....I am having a problem trying to connect to the internet... Even when i plug in the Ethernet cord it say i am sending out packages but not recieving any...and it is not working....
I have also tried to connect it to my router using the wireless connection and that wont connect either for some reason....I put in the WEP or whatever......and when i hit connect nothing happens do anyone know a answer to this....

to get wifi working use this:
follow directions dont assume you got it right, just make sure you get it right
[http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501)

---

### Post by redDEADresolve on 2007-01-09
anyone get beryl working yet?

---

### Post by redDEADresolve on 2007-01-12
I wrote a visual guide on my blogg about getting Ubuntu on the Dell 1501
Check it out for all things 1501 and Ubuntu

[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

---

### Post by redDEADresolve on 2007-01-24
got beryl working.

[http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html](http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html)

---

### Post by dashnak on 2007-02-08
> **redDEADresolve said:**
> got beryl working.

[http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html](http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html)


I followed your guide and it installed fine, I ran beryl, and I wept in awe at the beauty of it all....
 Then I tried to run it again, and my 1501 froze....
 And it kept happening on and off.....
 Eventually I discovered that if I reinstalled the apps mentioned in the guide, it would work for one boot, and the I would have to reinstall again....
 Now, after trying some other configs found in 2 different guides, it simply doesn't work.... beryl-manager loads, crashes, and reverts back to metacity....
 Also, even when it was working with the first guide, gnome-settings-daemon never loaded even though it was in my startup programs, I had to do it manually...
 Seem buying this laptop wasn't such a good idea after all, although everything else works great...
 Any thoughts on this?
I'm using an inspiron 1501, of course....

---

### Post by cw7585 on 2007-02-10
I had Beryl working, and was happily annoying my Mac colleagues with 3D bling when last week an update borked it. 

I think the way I got it going was so juryrigged that any little change easily knocked it over. I'm not moved to figure out what went wrong - I'm content to just run garden variety Metacity until Compiz/Beryl 3D implementations mature and the whole thing gets past its current "highly experimental" feel. Function trumps form.

---

### Post by Aruna on 2007-02-13
I'm afraid after updating the kernel the ATI propietary driver is not installed any more.
I get this after typing fglrxinfo:

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

### Post by Aruna on 2007-02-13
Just:

$sudo apt-get install linux-restricted-modules-$(uname -r)
$sudo depmod -a
$fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by golfing22 on 2007-03-26
Has anybody been able to get suspend/hibernate to work right on the Inspiron 1501?   Everything else seems to be working fine for me including wifi, beryl, even SD slot

---

### Post by dashnak on 2007-03-26
Nope, still searching for a way to fix that.... It would be awesome.....

---

### Post by mweichert on 2007-04-12
Do you know what changes need to be made to get beryl working with feisty?

Thanks,
Mike

---

