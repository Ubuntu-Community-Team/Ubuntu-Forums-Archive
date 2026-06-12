---
title: "Installing Ubuntu on DELL Inspiron 9300"
date: 2006-09-10
forum: Hardware &amp; Laptops
---

### Post by DyaruM on 2006-09-10
Hi, I'm trying to throw my windows xp away and start using linux ubuntu, the problem is that I don't know how to get the drivers working on ubuntu.

This is what my laptop is:

DELL Inspiron 9300

Processor: Intel Pentium M 1.6GHz
Memmory: 1024MB
Video Card: nVIDIA Ge-Force Go 6800
HardDrive: 100GB
17" widescreen (It needs 1440x 900 resolution)

I also need to fix some WiFi problems because it is not working

The touchpad is not working

I will also need help with the sound card which is a SIGMATEL

I will thank you for your help! :)

---

### Post by David Corrales on 2006-09-11
I have the same model (ati card and 1920x1600 though) but the wifi worked out of the box (including wpa!), touchpad does too with the vertical bar scroller and finally sound hasn't me given any trouble!
Are you just trying the livecd or have you already installed dapper to disk?

---

### Post by Peter41az on 2006-09-11
Well Sigmatel audio usually plays nice for me. so thats a good thing. from what i see, the wireless should work out of the box. are you sure its configured correctly? Video should be no problem, nor the touchpad.
Id say youll have a minimum of work :) 
Bravo to you for throwing away the Active x beast.

---

### Post by David Corrales on 2006-09-11
Got a higher res of that avatar picture? I'd like to check the assets :)

---

### Post by jimmygoon on 2006-09-11
> **David Corrales said:**
> Got a higher res of that avatar picture? I'd like to check the assets :)

I was thinking something along the same lines!

---

### Post by Pumm4 on 2006-09-11
On-topic:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

---

### Post by Peter41az on 2006-09-12
sorry! the laptop it was on was in my trunk when some idiot rearended me so her assets live on as long as i dont change the avatar heh :)

But, i think she was in Neon evangelion.... 

:)

---

### Post by David Corrales on 2006-09-12
I was talking about the Ubuntu booblets :mrgreen:

---

### Post by yeehawjared on 2006-09-12
your touchpad doesn't work?   I have a 9300 and the touchpad/wireless(WPA)/audio everything worked great

I got XGL/Compiz working flawlessly at one point, but the automatic updates killed something.  I'm still trying to figure out how to get XGL working again... anyone know how?   Also, I suggest using automatix.  Do some searches for it if you don't already know what it is.

---

### Post by DyaruM on 2006-09-12
Well, I am really noob using ubuntu, what do I need to do first and where I can Find what I need??

---

### Post by DyaruM on 2006-09-12
Shhhh es un secreto :P:P LOL

> **David Corrales said:**
> Got a higher res of that avatar picture? I'd like to check the assets :)

---

### Post by Peter41az on 2006-09-13
oh yeah, sorry. i mustve been really tired to miss those boobies lol

---

### Post by DyaruM on 2006-09-13
HOW DO YOU DO EVERYTHING, COULD YOU PLEASE EXPLAIN BY STEP?

> **David Corrales said:**
> I have the same model (ati card and 1920x1600 though) but the wifi worked out of the box (including wpa!), touchpad does too with the vertical bar scroller and finally sound hasn't me given any trouble!
Are you just trying the livecd or have you already installed dapper to disk?

---

### Post by David Corrales on 2006-09-13
> **DyaruM said:**
> HOW DO YOU DO EVERYTHING, COULD YOU PLEASE EXPLAIN BY STEP?

Well... wireless just worked (WEP and WPA!). The light doesn't but there's an easy way to check if it's working. Type **iwconfig** in a terminal and you'll see if the radio is on or off.

The sound worked out of the box, same for the vertical scroll bar :confused:

---

### Post by Belyel on 2006-09-13
> **DyaruM said:**
> HOW DO YOU DO EVERYTHING, COULD YOU PLEASE EXPLAIN BY STEP?

I'm gonna nitpick a second here first and say that shouting at the board is not the best way to get help, no matter how frustrated you are.  That being said, I just installed Ubuntu on a friend's laptop, a *lovely* Dell Inspiron 9300 running the nVidia graphics chipset.  Using Dapper, the sound and touchpad worked from the install.  But, I still haven't been able to get wireless working.  If you follow the link provided earlier in this topic, you can see that some other users got theirs to work by upgrading the kernel to 2.6.16, so that's what I'm going to try next.  You can find directions for upgrading the kernel [here.]("http://www.ubuntuforums.org/showthread.php?t=157560")

Best of luck, I'll keep people posted when I get a chance to work on the laptop again.

---

### Post by DyaruM on 2006-09-13
I did not mean to shout, I just put the letters a little bit bigger so they could call someone's attention. Because if you say "Ok, I installed ubuntu in my DELL Ins 9300 it works good, and everything else is good -- end of the topic" What does that help us??? If I knew how to do it I would say:

Step 1: Install WiFi using this link xxxxxxxx using a program called xxxxxxx

Step 2: Install the drivers of nVIDIA from this other link xxxxxxx

You know what I mean??? If someone can do it like that, I will apreciate it a lot THANKS!!!

---

### Post by yeehawjared on 2006-09-13
I just did a fresh install a few mintues ago.  I'm up and running with nvidia drivers and XGL/compiz on my inspiron 9300 with geforce go 6800


getting your NVIDIA driver to work is really easy:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

now make your default color depth 24 bit:
sudo gedit /etc/X11/xorg.conf

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV41.8 [GeForce Go 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    [COLOR="Red"]24[/COLOR]

restart

Now lets get XGL/Compiz fired up:
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
***use the SECOND HOWTO on that page.  It works perfectly, it was updated after the new compiz manager change to CSM

as for wireless and touchpad and vertical scrollbar - all of mine worked perfectly right out the box.  WPA even works out of the box... maybe re-install dapper from scratch, make sure the ISO's md5 hash matches before burning.

---

### Post by DyaruM on 2006-09-14
Thank you a lot yeehawjared, that is exactly what I need, now I will need to solve the other problems as Sound, WiFi, and Touchpad

---

### Post by yeehawjared on 2006-09-14
not sure if you've tried this - install automatix

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

There are a few networking options you can add - like WPA supplicant (i think) and a better WiFi selector thing.  I don't know the exact names but select those and install.  Take a look at all the things you can install - it makes setting up Ubuntu super easy.

---

### Post by yeehawjared on 2006-09-14
saw this on digg... could help you out with your wireless problems:
[http://www.linux.com/article.pl?sid=06/09/05/2055232](http://www.linux.com/article.pl?sid=06/09/05/2055232)

---

### Post by DyaruM on 2006-09-14
IT IS REALLY HELPING ME HEHEHE :D :D :D :D THAAAAAAANKS!!!!

now do you know how to fix the touchpad??

---

### Post by DyaruM on 2006-11-22
Hi, It's me again, does anyone know how to get WIFI working????:-({|=

---

### Post by yeehawjared on 2006-11-22
Dapper works perfectly right out of the box.  Edgy is a different story.

when I dmesg | grep 2200 I get an error saying:

ipw2200: Radio Frequency Kill Switch is On:

If I could change the kill switch to OFF I think it'd work.
please see the following thread:

[http://ubuntuforums.org/showthread.php?t=303135](http://ubuntuforums.org/showthread.php?t=303135)

---

