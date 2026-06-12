---
title: "Can't switch to 1680x1024 on my Dell 6400"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by couzin2000 on 2007-05-02
Hi all,
first time poster, but longtime fan of Linux (not a user though). I've had Feisty installed on my Dell 6400 laptop for 4 days now, and only one thing is bugging me: the screen resolution.

I have the built-in driver running for my Intel945GM card; the card was supported right out of the box. Screen is ok, but I'm limited to 1280x1024, which is not right -- I would like to use the entire potential of my screen.

I've read many posts in regards to editing xorg.something, but I'm a newbie when it comes to Linux so I need a little more than just a straight-up recommendation. If there's an update I can download thourgh the system update, then great - that's easy. If not, well I should tell you I don't know the first thing about *compiling drivers and kernels*, and stuff like that. I'm not afraid of it, but I'm a little unsure where to start.

I will keep reading other posts to find out more about zorg (or whatever it's called) and I'll await for anyone's help here. Let me know if I can offer any info that might give you a clue as to what I need to do. Thanks!

---

### Post by taurus on 2007-05-02
Just edit /etc/X11/xorg.conf 

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```
and try to add the resolution you want to use.  It should be near the end of it so just scroll down and you will see a bunch of lines.  Add the one you want in front of all those resolutions.  Save the change and restart X with

<Ctrl><Alt>Backspace

---

### Post by couzin2000 on 2007-05-02
Sounds easy enough... I'll try it and get back. 


Just one thing: do I need to know stuff like refresh rates, screen size ratio, voltage and stuff? I seem to remember seeing that in a posted xorg.conf file. 

Thanks!

---

### Post by taurus on 2007-05-02
You need to enter refresh rates in /etc/X11/xorg.conf to minimize or stop the flickering on the monitor.

---

### Post by couzin2000 on 2007-05-02
OK - tried it, no effect. Actually, I found 5 different 'depths' for 1680 by 1050, which was the ONLY resolution offered. Yet, in System/Preferences/Screen Resolution, I get 4 choices and none of them are 1680x1050.

I did save the file, ran it as root, and restarted X, but to no avail. What next? :mrgreen:

---

### Post by harold4 on 2007-05-02
Here's an example:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "card_1"
    Monitor        "HD_LCD"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection

```

Post this portion of your xorg.conf

---

### Post by couzin2000 on 2007-05-03
Yeah, that's about what I see. Actually, I have something like this:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "card_1"
    Monitor        "HD_LCD"
    DefaultDepth    24
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050"
    EndSubSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "card_1"
    Monitor        "HD_LCD"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "card_1"
    Monitor        "HD_LCD"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
```

You see how I have different depths of color? Each mode has the wanted resolution -- but in the GUI selector I can't see it, and instead I see 4 OTHER resolutions that I don't wanna use, and that aren't even present in xorg.conf.
Unless it's digging somewhere else for this data? What else should I be looking at?

---

### Post by couzin2000 on 2007-05-03
Ok - after modifying my xorg.conf and losing the entire GUI, then using [FONT="Courier New"]dpkg-reconfigure[/FONT], I'm NOW (finally) posting my current xorg.conf setting.

```

Section "Screen"
   Identifier           "Default Screen"
   Device               "Intel i945GM"
   Monitor              "Generic Monitor"
   DefaultDepth         24
   SubSection "Display"
          Depth         24
          Modes         "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
   EndSubSection

```
I wanted to remove the mentions other than 1680x1050, but it just doesn't matter -- the system won't bring it back when I'm in X, and won't give me the choice of resolution.

Would there be necessity to specify a driver other than "Generic Monitor"? like installing somekind of driver for the Dell WXGA screen I have built into my Inspiron 6400? I'm not used to Linux, but I know in Windows it needs to be done most of the time. "Default Monitor" will work, but will not handle big-time resolutions.

Am I making any sense here?

Please help (yet again)!!

---

### Post by jjordan on 2007-05-03
Variations on this issue are popular topics.  A quick search indicates that your laptop has an Intel 950 video "card" which is a derivative of the i915.  These video "cards" are very popular with laptops, work well and are actually supported well in Linux.  It sounds like you need to use i915resolution to add the resolution you want to use to the "card's" BIOS.  search for i915resolution on this forum and you will find some other postings about how to get this set up. There is a very nice howto.

-j

---

### Post by couzin2000 on 2007-05-03
Well, I think that's a good thought process, only I'm just a little bit unsure where you got the fact that I use a i950. My card is actually an **Intel i945GM** - this I know from looking at my bill from Dell and from having run the driver in Windows for at least a year now.
Now, if the i950 you were referring to is the same thing, or is handled by the same driver, well I can say I already have the built-in driver running it as i945GM and it seems to work fine -- which is why I'm asking the question first and foremost: I can see the text in xorg.conf, and it says nothing about resolution in the video card's config -- however all the resolutions available are mentioned in the screen's config.

Granted I don't know the first thing about programming drivers, but since the text is like that, shouldn't it be the screen's driver that determines what I see? It sorta sounds more logical to me.

Please correct me if I'm wrong. And thanks for the info, I will nonetheless start investigating that alley.

---

### Post by couzin2000 on 2007-05-03
oh - you know what? I think I misunderstood the whole sense of your reply. If I now understand correctly, you're saying the video card's BIOS needs to be updated because the driver is reading straight to the BIOS and foregoing xorg?
I'll go and read the Howto, and see what I can see. Thanks for the tip off!

---

### Post by couzin2000 on 2007-05-03
I found the Howto, and it looks promising - as in VERY. I need to read it again (not diagnoally) to better assimilate it before doing it, but I think it'll be fine. I'll confirm when all this is up and running. Thanks again!

---

### Post by matburton on 2007-05-03
Both I and my house mate have an i915, he has the same variant as you. Anyway the resolution thing is pretty easy to fix:

```
sudo apt-get install 915resolution
```

Then log out and hit CTRL-ALT-BACKSPACE. Hopefully when you log back in you'll either be at the correct resolution or will have the option for the correct resolution in SYSTEM -> PREFERENCES -> SCREEN RESOLUTION.

Hope that helps if you didn't already get it sorted ;)

(You should make sure that your xorg.conf has the correct resolutions if you haven't already)

---

### Post by couzin2000 on 2007-05-03
It WORKS!!
Thanks so much!!

---

### Post by jjordan on 2007-05-04
Glad you got it working, the "card" does not ignore the xorg file, the driver has to ask the "card" what resolutions are available so i915resolution is just substituting your values in for a couple of unused values, has to do it each time you boot.  It is not always as easy as simply installing i915resolution.  I had to do quite a bit of init file editing to get my Fujitsu P1510 to support my external 1680 X 1050 monitor.  Thanks for posting back that it worked.

-j

---

