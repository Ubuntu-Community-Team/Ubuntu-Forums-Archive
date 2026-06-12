---
title: "How to pass xorg options in Ubuntu Lucid?"
date: 2010-05-19
forum: Hardware
---

### Post by bkruggel on 2010-05-19
Hello,

I freshly installed Ubuntu Lucid, first experience with Ubuntu, because I have always been living in the past with Debian stable...
I've just bought a new mouse with a tilting wheel and when I arrived home I was already crying when I saw that there are no button events associated to moving the mouse wheel left or right, but rather some three-dimensional stuff I don't really find useful.
(Moving to the wheel to the left in "xinput test", for example is this: motion a[0]=873 a[1]=667 a[2]=-1 - while a2 decreases when I click to the left, and increases when I click to the right).

I have found a thread, here, that explains the options you need to set in order to make this work:
[http://ubuntuforums.org/showthread.php?t=217086](http://ubuntuforums.org/showthread.php?t=217086)
(Although I have the Comfort Mouse 4500, the post concerns the 3000 but still - they came out at the same time, so there's probably the same stuff inside).

These are 3 lines to put into xorg.conf.

Unfortunately, Ubuntu Lucid does not seems to read anything about input devices that you would like to put into /etc/X11/xorg.conf (Although the wiki [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid) says to put input options into the file -- ??? -- they are there now, but happily)

So I searched a while and I have tried the /etc/hal/fdi/policy scripts as well, in order to pass options through HAL, but completely ignored as well.
So I tried the /etc/X11/xorg.conf.d/ option, which brings up some strange errors about USB devices (I don't really find these errors in the logs...) and gdm won't start.

So here the content of the file in /etc/X11/xorg.conf.d/01-mouse.conf (commented out, for the moment, as the system won't start otherwise).

#Section "InputDevice"
#    Identifier "Configured Mouse"
#    MatchIsPointer "on"
#    MatchDevicePath "/dev/input/event*"
#    MatchProduct "Microsoft Microsoft® Comfort Mouse 4500"
#    Driver "evdev"
#    Option "CorePointer"
#    Option "DIALRelativeAxisButtons" "7 6"
#    Option "WHEELRelativeAxisButtons" "4 5"
#    Option "ZAxisMapping" "4 5 6 7"
#EndSection

Am I doing something wrong here or is there simply no way anymore to pass options about input devices to X?
By the way, even the horizontal scroll does not work out of the box, and I have a widescreen high resolution screen, so horizontal scroll seems a little bit 1998 to me. I'd rather configure the left-right-tilt of the mousewheel through imwheel and control the volume while I listen to music, fly through the tabs in Firefox, whatever you name it.

I also tried gpointing-device-settings, but it ends with a segmentation fault and there are some bugs already filed.

Finally, is this an expected behavior? I do believe that it should be simpler than that. The user should be able to edit /etc/X11/xorg.conf and the system does it's best to grant these wishes.

Thanks for your help and time,
Björn

---

### Post by jyaan on 2010-08-10
I bought that exact same mouse today, and so I'm having the same problems. I also looked at several threads (the one that you listed was the most promising of those I found), but nothing has worked. If I run xev, I noticed that neither button nor axis is identified -- only that there is mouse motion.

---

### Post by bkruggel on 2010-11-03
And I just found out last week how to do it :-)

Btnx can recognize these mouse buttons, so I have btnx and imwheel running at the same time. I can't use the horizontal shift in imwheel, but I can change tabs in Firefox and keep the thumb buttons free for other functions.

sudo apt-get install btnx

and

sudo btnx-config

And follow the stuff. If you're doing it like me, you probably only want to let btnx control the vertical scroll buttons. Although, if you don't care to associate mouse buttons with modifiers in order to have it execute differents commands, btnx will be all you need (with imwheel, for example, you can define things like: turning the wheel down with ALT pressed means Page_Down, turning the wheel down with CTRL pressed means End, etc).

---

