---
title: "How to get an Acer 5310 working on Linux"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by p1r0 on 2008-01-06
Well, it took a long time to get my Acer 5310-2553 working properly on Linux so when I finally got it I decided to write this mini how to.

[SIZE="5"]THE SOUND[/SIZE]

The first problem was that there was no sound whatsoever but the sound icon was and according to the os the driver was fine.

To fix the sound follow the instructions found on [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
in the *Update to the Latest Version of ALSA* section and only that.

After doing the alsa update edit the /etc/modprobe.d/alsa-base.
You can do it with:
```
sudo nano /etc/modprobe.d/alsa-base
```
or
```
sudo vi /etc/modprobe.d/alsa-base
```

or more friendly with:
```
sudo gedit /etc/modprobe.d/alsa-base
```

and add the line:
```
options snd-hda-intel model=acer
``` 
at the end and save.

Reboot.

And that's it for the sound.

[SIZE="5"]Wi-Fi[/SIZE]

Ok, now wireless networking. This was a tricky one.

After trying with a LOT of different versions of MadWifi I gave up and decided to try ndiswrapper. 
I did it with my windows drivers and it didn't work so I googled and googled and finally found a post here that had some older windows driver for my AR5007EG Atheros card.
Sadly I can't find that post again so I will attach the driver here.

NOTE: If you know what the post is please tell me so I can give the author credit for it as 
this solution is not mine.

The thing goes like this, first make sure you've got ndiswraper and if not install it.
And the use the driver attached to this post. And you've got Wifi!

[SIZE="5"]The Touchpad[/SIZE]

Ok, now onto the final touches...
When I thought that everything was sorted out my touchpad started acting crazy. It
click anywhere and everywhere just by trying to move the cursor around.

The problem was that the OS detected it as Synaptics and it was Alps. So I googled again and I found a solution here: [http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/]("http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/")

The only thing I needed to do far from that was to modify the *Section "ServerLayout"*
section to set 
```

InputDevice     "Synaptics Touchpad" 
``` 
to
```

InputDevice     "Alps Touchpad"
```


Well, that's it. The built in webcam I can't get working....but the notebook is completely 
operational now!

If you see any error please post the corrections.

Enjoy!

---

### Post by dominik_ap on 2008-02-10
Hi i have discovered this topic... So I tried to follow your guide, but it didnt help me...

Sound:
its not working, i have installed Alsa (driver, lib, util) v.1.0.16 and when typing alsamixer i see 2 things which are unmuted...

But i cant controll my Sound on/off  by button FN + F8 and  buttons FN + Play/stop/next/prev are not working
And also the scroll button on the left side of the laptop stopped working, i dont know where is the problem.


WIFI:
I have succesfully installed the driver by ndiswrapper, so when i type iwconfig i see wlan0 finaly.
But i dont know how to connect to any wifi network, can you help me some GUI tool or commands in console?


TouchPad
I tried your help, it looks much better, but sensitivity is too low, i need to increase it much much more, i didnt find any help by man synaptics...
can you tell me which of these lines is it? And should i restart notebook or just Xserver?


Thank you for this topic, I hope we will provide here some information for the Laptop Acer Aspire 5310 on Ubuntu

---

### Post by Tobi-fp on 2008-02-10
Great job mate, maybe you should post it in the laptop testing team section too?

---

### Post by p1r0 on 2008-02-10
Hi dominik!

> Sound:
its not working, i have installed Alsa (driver, lib, util) v.1.0.16 and when typing alsamixer i see 2 things which are unmuted...

But i cant controll my Sound on/off by button FN + F8 and buttons FN + Play/stop/next/prev are not working
And also the scroll button on the left side of the laptop stopped working, i dont know where is the problem.

I had that problem myself recently (except that my sound works perfectly) when I messed up my linux completely and had to reinstall, If I remember correctly (this may not work) the first time I downloaded the 1.0.15 version of alsa driver/util/lib and that time my scroll and on/off button worked just fine. This time I tried the 1.0.16 rc and they don't. I haven't had the time to try the 0.15 again, so I don't know for a fact if this is the issue.
As for the multi media keys mine don't work either but I think that this has nothing to do with alsa.

> I have succesfully installed the driver by ndiswrapper, so when i type iwconfig i see wlan0 finaly.
But i dont know how to connect to any wifi network, can you help me some GUI tool or commands in console?

Well I know this via GUI. If ndiswrapper is installed correctly (I don't exactly remember how to do this, but if you don't find info let me know and I'll try to remember where I saw a good howto on the web about this) left clicking (once) on the networking gnome panel applet (by the clock) should give you the option "Connect to other wireless network" and then it will ask for the connection details, fill them in and that should do it.

> TouchPad
I tried your help, it looks much better, but sensitivity is too low, i need to increase it much much more, i didnt find any help by man synaptics...
can you tell me which of these lines is it? And should i restart notebook or just Xserver?

I think that this lines do it:

```

Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
```

I must say that I don't know this for sure and don't know which are the correct values. So if you try it first BACK up your xorg.conf file. 
And just restarting X should do it (I think ;) not very sure about things today).

Well I REALLY hope this helps. Please post the results!!!

---

### Post by dominik_ap on 2008-02-11
[SIZE="4"]SOUND[/SIZE]
> **p1r0 said:**
> 
I had that problem myself recently (except that my sound works perfectly) when I messed up my linux completely and had to reinstall, If I remember correctly (this may not work) the first time I downloaded the 1.0.15 version of alsa driver/util/lib and that time my scroll and on/off button worked just fine. This time I tried the 1.0.16 rc and they don't. I haven't had the time to try the 0.15 again, so I don't know for a fact if this is the issue.
As for the multi media keys mine don't work either but I think that this has nothing to do with alsa.

Hm i have already tried Alsa v 1.0.15 and 1.0.16, but both Full versions, not the RC. And nothing.

You know its strange, i think my laptop is Muted, but alsamixer doesn't show it and i can't unmute it when the key FN+F8 does nothing. But FN+F7 turns off/on my touchpad, so the keys are in general working but not these connected with sound.

I was trying also to install some patches "realtek10-17.tar.gz" but after applying them i wasnt able to compile ALSA driver.

and also i tried this guide:
*[http://ubuntuforums.org/showthread.php?t=545697](http://ubuntuforums.org/showthread.php?t=545697)*
but it didn't work after it.

[SIZE="4"]WIFI[/SIZE]
> **p1r0 said:**
> 
Well I know this via GUI. If ndiswrapper is installed correctly (I don't exactly remember how to do this, but if you don't find info let me know and I'll try to remember where I saw a good howto on the web about this) left clicking (once) on the networking gnome panel applet (by the clock) should give you the option "Connect to other wireless network" and then it will ask for the connection details, fill them in and that should do it.

Well my problem with UBUNTU is, that i dont have these icons of networkmanager and other stuff which should be near to clock (i have just clock, date, opened programs and KMenu, Network fles).
It has just disappeared and i dont know how to get back these icons :) (it happened when i installed KDE4, first my Panel disappeared, so i have to add it again (i dont remember how) and after i had to add clock, panel with opened windows and so, but i didnt find icons)

I am now trying the program Wicd which i downloaded via:
```

sudo mcedit /etc/apt/sources.list

```
 there I added:
```

deb http://apt.wicd.net gutsy extras

```
and continued with these commands:
```

sudo apt-get update
sudo apt-get install wicd

```
Go to KMenu -> Internet -> Wicd to run it or start Katapult and write "wicd"

I can see now some WiFI networks here, so I will try it later when i will be at some Free Wifi to connect.
I will inform you, but this program seems to be very easy and including all functions i need (it can connect your laptop to wifi AND to wired network)

[SIZE="4"]TOUCHPAD[/SIZE]
> **p1r0 said:**
> 
I think that this lines do it:
```

Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
```

I must say that I don't know this for sure and don't know which are the correct values. So if you try it first BACK up your xorg.conf file. 
And just restarting X should do it (I think ;) not very sure about things today).

Well I REALLY hope this helps. Please post the results!!!


Hey thanks, it helped, first i had these values in different section (in file **/etc/X11/xorg.conf** ) as it was shown here:
*[http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/](http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/)*
other help is here:
*[http://ubuntuforums.org/showpost.php?p=466023&postcount=50](http://ubuntuforums.org/showpost.php?p=466023&postcount=50)*

But I deleted the second Section "InputDevice" and left just first so the code is now:
```

Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event4"
        Option          "Protocol"              "event"
        Option          "HorizEdgeScroll"       "0"
        Option          "MinSpeed"              "0.50"
        Option          "MaxSpeed"              "0.80"
        Option          "AccelFactor"           "0.030"
        Option          "SHMConfig"             "on"
EndSection

```

And don't forget that you have to change also section "ServerLayout":
```

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
      **  Inputdevice     "Alps Touchpad"**
EndSection

```

PS: Do you think if somewhere here on ubuntuforum is some "official" section for help with ACER 5310? Because I d like to help some people with starting with this laptop and ubuntu and add there what I found on the internet (links, helps, how to) for the stuff running (touchpad, wifi).
I will do it on my personal site for sure, i will post the link later...

---

