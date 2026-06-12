---
title: "Trouble with Wacom"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by imagxz on 2009-06-11
I am trying to get a Wacom Artpad II working. It's a serial connection but i have a keyspan adapter to make it usb. Also i just formatted with ubuntu and have **no idea what im doing**. Can anyone help me out with this?

---

### Post by jerrrys on 2009-06-11
you may not want to go there till you get some experience...

[http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)

---

### Post by Favux on 2009-06-11
Hi imagxz,

It is important for you to let us know which version of Ubuntu you are using.

In the meantime you may want to start looking over Loic2's Wacom wiki here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by imagxz on 2009-06-11
I am using Ubuntu 9.04, in the meantime I will read these...

---

### Post by imagxz on 2009-06-11
Installed wacom-tools and xorg so far...So im trying to edit xorg.conf.
So in this guide... [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)

Why are there many sections titled:
Section "InputDevice" 

Which ones am I supposed to use?

This is how my xorg.conf looks like
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

Anyone?

---

### Post by Favux on 2009-06-11
Hi imagxz,

In Jaunty you no longer use the xorg.conf to configure Wacom.  You use the HAL/.fdi method.  The 10-wacom.fdi is in "/usr/share/hal/fdi/policy/20thirdparty/".

If you're tablet is recognized by the .fdi it should be active after booting.  I don't know how your tablet will set up using the usb adaptor.  Have you tried just using the serial connection?  If things are working you should get some activity.  Then to figure out what's happening we need to look at the output of a couple of commands.
```
xsetwacom list
```
When that's returning things like stylus, eraser, cursor, and pad we're golden.  Also:
```
xinput --list
```

What does an Artpad II have?  Stylus, stylus buttons, eraser, Wacom mouse, pad?

---

### Post by imagxz on 2009-06-13
Wow, I didnt see anything about not using xorg.conf when it comes to wacom on the forums.
This tablet has the stylus, 2 buttons, eraser, and pad.

Here is what I get with those commands...

```
xsetwacom list
``````
Data incomplete in file /etc/X11/xorg.conf
    Device section "Configured Video Device" must have a Driver line.
Problem when parsing config file
```and for...

```
xinput --list
``````
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Kensington      Kensington USB/PS2 Wheel Mouse"    id=5    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=6    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1

```

Any ideas?

---

### Post by Favux on 2009-06-13
Hi imagxz,

OK, it looks like your tablet isn't detected.  I think you can ignore the video stuff "xsetwacom list" returns.  Just to be sure you now have both linuxwacom packages installed through Synaptic Package Manager, right?  The xserver-xorg-input-wacom and wacom-tools?  Is the tablet attached through the serial cable or did you use the keyspan adaptor to make it usb?

I guess I would try it both ways.  Turn it off and use one connection and run "xinput --list" after it boots.  Turn it off and try the other connection and xinput.  You are looking for at least a stylus section.  My guess is your best bet is with the serial connection.  Here's a thread about setting it up with an earlier version of Ubuntu:  [http://ubuntuforums.org/showthread.php?t=534174](http://ubuntuforums.org/showthread.php?t=534174)  They're using xorg.conf of course, which won't work for you in Jaunty.  Or maybe it would if you compiled a recent version (0.8.3-2 and up) version of linuxwacom replacing the special default 0.8.2-2 version in Jaunty.

So how old is the Artpad II anyway?  In other words what year did it come out?  Was it for PC or Mac or both?

Edit:  Not to discourage you but I'd feel better if the LWP said it supported the Artpad II.  It doesn't seem to show up in it's list of supported tablets on the lower left here:  [http://linuxwacom.sourceforge.net/index.php/main](http://linuxwacom.sourceforge.net/index.php/main)  Maybe it had another name (UD series or PenPartner)?  And we do know from the thread above some folks got it working with linuxwacom drivers.

---

### Post by imagxz on 2009-06-27
Sorry for the long wait, here is what I ended up doing.
Installed Sun Virtualbox with a version of XP SP2,Photoshop,Illustrator, and Autodesk Sketchbook pro(those substitute GIMP and Inkscape even though I was fine using them)

Installed the XP wacom driver and the program for my Keyspan Serial port to USB

Disabled mouse integration early in the boot up of XP and viola! Wacom Artpad II works perfectly, can set and use all shortcuts,buttons, and sensitivity works. 

I would suggest this to anyone who wants to set up an old wacom on Ubuntu

---

