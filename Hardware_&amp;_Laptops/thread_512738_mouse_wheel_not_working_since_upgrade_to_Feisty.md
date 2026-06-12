---
title: "mouse wheel not working since upgrade to Feisty"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by The Judderman on 2007-07-29
Hello...

I realise that this issue has already been raised, but I have an added complication. Just recently had a virtually seamless transition from Edgy to Feisty. everything has been great, and I am loving Ubuntu more and more... The only thing that I am struggling with (and I agree it is minor!) is that the wheel on my laptop mouse doesn't seem to work any more... I have a HP Compaq nx6110 laptop, and it was working beautifully on its own in Edgy (better than in windoze!)

I have seen many posts which say to tweak the /etc/X11/xorg.conf file... Unfortunately, in my case this file is empty (maybe the source of my problems?), so there is nothing to tweak...

Any ideas?

Much appreciated.

The Judderman

---

### Post by benanzo on 2007-07-29
Is it an external mouse or a touchpad?  If it's a touchpad then have a look [here]("http://ubuntuforums.org/showthread.php?t=493758") for how to setup the synaptics driver to get scrolling/tapping etc.

If it's an external mouse make sure your "mouse" section in **/etc/X11/xorg.conf** looks like this:
```
Section "InputDevice"
        Identifier      "External Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

Good luck!

---

### Post by The Judderman on 2007-07-29
It's a touchpad, so I'll have a look at the thread. As I pointed out in my original posting, my /etc/X11/xorg.conf file is bizarrely empty!!!

---

### Post by The Judderman on 2007-07-29
Your thread looks like it is just what I need, but I have an empty /etc/X11/xorg.conf file... I don't know how this file is generated, but somehow it wasn't when I installed Feisty... Any ideas?

---

### Post by benanzo on 2007-07-29
I am surprised that you're able to get to the desktop with your xorg.conf file empty!

Anyhow, you can recreate it by doing:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
in a terminal.

---

### Post by The Judderman on 2007-07-29
when I recreated the file, I then rebooted and couldn't load X due to some bad configuration of the visual stuff. I obviously chose the wrong driver, but not sure how to find out what is the right one for my video card. I think that I have an intel graphics card, but how do you find out the correct X driver?

In the recovery mode, I deleted that file (/etc/X11/xorg.conf) and rebooted into gnome with no problems!!!!

How bizarre....

---

### Post by The Judderman on 2007-07-30
Benanzo, thanks for your help... I worked out that I needed the i810 driver, and configured the /etc/X11/xorg.conf file, and just from doing that ( i had already installed the synaptics stuff), the mouse is now working perfectly...

I am very happy with Feisty, and maybe I need to do a post at some point, to show people how easy it really is to install and use Ubuntu, coming from a noobie's perspective!!

Thanks for your help anyway... Couldn't do it all without the help of the Community!!!!!

A very happy Judderman

---

### Post by benanzo on 2007-07-30
Good work!

---

