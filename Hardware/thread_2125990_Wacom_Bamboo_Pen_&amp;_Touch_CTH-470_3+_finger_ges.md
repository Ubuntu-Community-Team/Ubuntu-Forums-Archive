---
title: "Wacom Bamboo Pen &amp; Touch CTH-470 3+ finger gestures"
date: 2013-03-15
forum: Hardware
---

### Post by Sirolf10 on 2013-03-15
I've posted this before on [Ask Ubuntu]("http://askubuntu.com/questions/245470/wacom-bamboo-pen-touch-cth-470-3-finger-gestures"), but after one response which didn't solve it and some waiting, I decided to ask it here, too.

I love my CTH-470 and I'm glad it works without having to spend hours in the terminal (since I believe 12.10, which I'm running now*). But in the [manual]("http://www.wacom.com/~/media/Files/Manuals/Bamboo%202011%20Users%20Manual.pdf") it states that you can swipe with three or even four fingers. However, I can't seem to find how to 'activate' this in Ubuntu. Is this even possible? If yes, how? And if no, are there any plans to support this in the future?

*I'm running Ubuntu 12.10 Quantal Quetzal 64bit, with Gnome 3.6.2

---

### Post by Favux on 2013-03-15
Hi Sirolf10,

Because you are using Gnome rather than Unity you do not have the default Unity multifinger system gestures.  You'll probably need to install touchegg.

I've done some investigation of the use of a multifinger BambooPT in Ubuntu.  It can get a bit complicated.  See part X., the multifinger multitouch section, of the updated [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").  Skim through that and maybe check out a few of the links.  I haven't yet tried touchegg in the Gnome Desktop but since it works with KDE I think it should work in Gnome.  Also see the Linux Wacom Project wiki's Multitouch page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch)

---

### Post by Sirolf10 on 2013-03-16
Hey Favux,

Thanks. There is a problem, however. I installed touchegg following [http://task3.cc/1068/os-x-like-multitouch-gestures-for-macbook-pro-running-ubuntu-12-10/](http://task3.cc/1068/os-x-like-multitouch-gestures-for-macbook-pro-running-ubuntu-12-10/), but it's not working yet; running touchegg in the terminal returns
```
Reading config from  "/home/floris/.config/touchegg/touchegg.conf" Try to make a multitouch gesture. If everything goes well the information about the gesture must appear 
[+] Avaliable gesture: 
     Name ->  Flick 
[+] Avaliable gesture: 
     Name ->  Drag 
[+] Avaliable gesture: 
     Name ->  Pinch 
[+] Avaliable gesture: 
     Name ->  Rotate 
[+] Avaliable gesture: 
     Name ->  Tap 
[+] Avaliable gesture: 
     Name ->  Touch 

```
But no matter what gesture I make, nothing happens.

I've tried running ```
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger touch" Gesture off
``` which only caused my tablet to only translate my moving finger to the moving of my cursor, but no clicking could be done (except for the 4 buttons and my pen, they still worked fine).

Running ```
synclient TapButton2=0
``` as suggested at the Linuxmint-forum-thread resulted in the error ```
Couldn't find synaptics properties. No synaptics driver loaded?
```

The thread also states that you should run ```
sudo apt-get install build-essential libqt4-dev utouch libx11-6 libxtst-dev libgeis-dev libqt4-qt3support qt4-linguist-tools qt4-qmake libutouch-geis-dev
``` but that returns the following:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package libutouch-geis-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgeis-dev:i386 libgeis-dev


E: Unable to locate package utouch
E: Package 'libutouch-geis-dev' has no installation candidate
```
After some research I found that utouch has been deprecated ([https://code.google.com/p/touchegg/issues/detail?id=169](https://code.google.com/p/touchegg/issues/detail?id=169)). Also, my tablet is not listed here [https://wiki.ubuntu.com/Multitouch/HardwareSupport](https://wiki.ubuntu.com/Multitouch/HardwareSupport), at least not with 3+ fingers. Does this mean it won't work or should it be solvable?

---

### Post by Favux on 2013-03-16
OK, a bunch of stuff to work through.

First thing is I don't believe we have to worry about [https://wiki.ubuntu.com/Multitouch/HardwareSupport](https://wiki.ubuntu.com/Multitouch/HardwareSupport).  I verified the third generation BambooPTs work fine with the 3 and 4 finger Unity system gestures when the BambooPT has wacom driver gestures turned off and/or is on the synaptics driver.  I'm thinking if the Unity gesture engine (with the utouch stack) is recognizing the BambooPTs multifingers then touchegg (with the utouch stack) will too.

Instruction-wise it is good to know utouch is deprecated in Quantal.  The instructions from the OS-X tutorial are pretty straight foward.  Did you try using the touchegg from the repository (Software Center) first?

I thought the default on the Wacom X driver was one finger tap was a left click even when gestures were turned off.  But maybe that only applies to the tablet PCs with only 1 finger touch.  Something to clarify.

But if turning off gestures disables 1FGT left click that's a problem.  Unless touchegg.conf can handle single finger?  Something like:
```
<touchégg>
    
    <settings>
        <property name="composed_gestures_time">0</property>
    </settings>
    

    <application name="All">

        <gesture type="TAP" fingers="1" direction="">
            <action type="MOUSE_CLICK">BUTTON=1</action>
        </gesture>
        
        <gesture type="TAP" fingers="2" direction="">
            <action type="MOUSE_CLICK">BUTTON=3</action>
        </gesture>
. . . 


```

---

### Post by Inoki on 2013-03-16
Maybe a bit off-topic: **@Favux** you mentioned, that in KDE tablet config works as it should? I'm asking coz I'm running Xubuntu, but that doesn't have any tablet GUI configurator whatsoever and I'm not even sure will it have one in the near future. I also saw that KDE has better font management, which makes it the perfect multimedia desktop for artists.

I own a **[Wacom Bamboo Manga]("http://www.wacom.eu/index2.asp?pid=294&spid=5&lang=en")**.

---

### Post by Favux on 2013-03-16
Hi Anathaen,

Just a bit.  :)

But yeah, the KDE Wacom applet appears to work about as good as the Gnome applet.  Actually I should put that the other way around because the Gnome applet is the late comer.  The KDE dev.s are active, one was just getting something cleared up on linuxwacom-discuss the other day.  They are switching it over to using libwacom I think, instead of their own tablet data base.  Plus I think there was a bug with the one installed by default in KDE Precise which rendered it non-working.  So you might have to install a more recent version.  But from what I can tell the dev.s respond to questions pretty well and are helpful.

---

### Post by Sirolf10 on 2013-03-16
Nope, I hadn't, since I had read (can't remember where at the moment, probably at an issue of the touchegg-project) it didn't work. I just tried and it indeed didn't work. It installed v1.0 instead of v1.1.1 and running it now returns
```
Reading config from  "/home/floris/.config/touchegg/touchegg.conf" Segmentation fault (core dumped)

```
So I sudo apt-get remove'd it and re-sudo make install'ed it. Should I try something with the synaptics-driver?

---

### Post by Favux on 2013-03-16
OK, I'm assuming you have a working touchegg again.

You could try synaptics but first let's check what version of xf86-input-wacom you are using.  What is the output of the following command in a terminal?
```
xsetwacom -V
```

---

### Post by Sirolf10 on 2013-03-16
Okay! Yes, it's in the same state as before trying the repository-version. xsetwacom -V returns 0.17.0.

---

### Post by Favux on 2013-03-16
Alright, xf86-input-wacom-0.17.0 is the Quantal default version and is likely the problem.  The xsetwacom Gesture parameter has been present quite a while.  The new behavior with **Gesture off** is that the touches get passed to the X Server.  That starts with 0.18.0.  That's what touchegg needs.  So you need to update to at least 0.18.0.  I would follow part II. of the BambooPT HOW TO I linked you to earlier and install the recently released xf86-input-wacom-0.20.0.  Or if you prefer clone the git repository.  By the way Ubuntu calls it the xserver-xorg-input-wacom package.

---

### Post by Sirolf10 on 2013-03-16
Yes! I've got it working now, updating to xf86-input-wacom-0.20.0 (and turning Gesture off) did the trick, thanks a lot!

---

### Post by Sirolf10 on 2013-03-16
One last question, the scrolling and right-clicking of touchegg are not that great -when you release your fingers after scrolling it sometimes scrolls back and you can't right-click and move your cursor directly afterwards anymore, you have to lift your finger first- so I wondered if it's possible to direct (1 and) 2-finger gestures to the xf86 and 3+ to touchegg?

---

### Post by Favux on 2013-03-16
Great!  Glad it is working now.  :)

> if it's possible to direct (1 and) 2-finger gestures to the xf86 and 3+ to touchegg? 
I don't think so.  See the gesture engines have to detect a touch and then wait for another touch or touches to see if it is a gesture.  So you can't really split that between different software unless they were specifically written to share that kind of information.  I'm pretty sure that's the difficulty.  Also implicit in that is that there are some timing settings.  It seems to me the gesture editor showed at least one timing setting.  I'd have to boot my KDE install to check.  If so maybe playing with that could help?

---

### Post by Sirolf10 on 2013-03-16
Oh, I understand. And yes, you can change the 'Composed Gesture Timeout', but as far as I can see that only influences the time it takes for the right-click-menu to show up, so that doesn't help.

---

### Post by Favux on 2013-03-16
Alright.  The xf86-input-wacom driver has some other parameters that can be varied like Scroll and ZoomDistance and TapTime.  I'm nearly done with what I was working on so I should be able to boot into KDE and checkout what if anything is available for touchegg.  Maybe we'll need to make some feature requests to the touchegg dev.s to allow us some method to change some of the gesture default settings.  We should check out their wiki too I suppose.

---

### Post by Favux on 2013-03-16
In touchegg-gce I see, when I check the "Show Advanced" box, a Composed Gesture Timeout.  But it looks like a general setting that applies to everything.  But worth checking out.  Also an unimplemented native one finger override.  So it does look like touchegg can handle single finger if need be.

I suppose another option would be to use one of the xinput Device Acceleration settings and see if that influences how touchegg handles the BambooPT's touch input.

---

