---
title: "Original wacom settings in Karmic"
date: 2010-02-15
forum: Hardware
---

### Post by jlarmour on 2010-02-15
Ok, I'm working on a tablet pc (Itronix ix325)  Everything was working until I tried to set the pen's second button, I have messed with it to much now.  How do I set everything back to the original wacom settings for Karmic?   I'm not even sure where I was or what I did at this point......  Was working, just no right click with the second button on the pen.  Now I have no wacom at all.   HELP!!   (way newbie!!)

---

### Post by Favux on 2010-02-15
Hi jlarmour,

Welcome to Ubuntu forums!

Did you try to compile linuxwacom?  Can you remember anything you did?

Let's look at the output, in a terminal, of:
```
xinput --list
```

---

### Post by jlarmour on 2010-02-15
Thank you for replying, I honestly do not remember exactly what I have done at this point, I did try to compile a new driver after it quit working.  But it was a cut and paste mess that I was trying.  



jeromy@itronix:~$ xinput --list
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
"Sleep Button"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Dell Dell USB Keyboard"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"No brand 2Port KVMSwicther"    id=8    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"ImExPS/2 Generic Explorer Mouse"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 13
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
"Macintosh mouse button emulation"    id=10    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
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
"Logitech Optical USB Mouse"    id=11    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 7
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
jeromy@itronix:~$ 
  

I had added into the xorg.conf file but I removed what I had added, it looks like this right now.

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by Favux on 2010-02-15
Hi jlarmour,

Do you know if the internal connection to your Wacom digitizer is usb or serial?  And you are sure it is a Wacom digitizer?

Right now there is no sign of your tablet in xinput.

What version of linuxwacom did you try to compile and from which HOW TO?

In Karmic while you can use the xorg.conf you should really use a wacom.fdi.  Where .fdi = device information file.

I noticed that your xorg.conf shows you don't have a video driver for your video chipset which is why it is using VESA.  If you don't know your chipset enter in a terminal:
```
lspci | grep VGA
```

PS:  You can "box" your output by placing it between the code tags, the # on the upper right.

---

### Post by jlarmour on 2010-02-15
I think it was this one:
[https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver)

I'm not sure now I have looked at so many and confused myself.

Here is the chipset--  this must be why I can't rotate the screen, that is my next task once I fix this uh-oh.
```
jeromy@itronix:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
jeromy@itronix:~$
```J

---

### Post by jlarmour on 2010-02-15
I don't know what I did the first time, but I redid the [https://help.ubuntu.com/community/Wacom/LatestDriver ]("https://help.ubuntu.com/community/Wacom/LatestDriver")
Now my pen is working again.  Do you want me to repost the first request?  I still need no make the button on the side of the pen the right click.  I'm sorry I'm so new at this but it is a blast to learn...

---

### Post by Favux on 2010-02-15
Hi jlarmour,

OK, that's a pretty old version of linuxwacom and if that is the version you used I don't think it would compile or install because it doesn't support Xserver 1.6.  Were you able to?:
```
sudo make install
```
Or did you do the uninstall commands?:
```
cd Desktop/linuxwacom-0.8.1-6/prebuilt
sudo ./uninstall
```

Let's see what the output of this is:
```
grep -i name /proc/bus/input/devices
```

Right, let's hold off on the video stuff.  At least now you have keywords to search with.

Edit:  Oops you posted again.  I don't understand that.  Try in a terminal:
```
lsusb | grep [Ww]acom
```

---

### Post by jlarmour on 2010-02-15
used the driver 0.8.5.10 not the older one that was listed this time.  I think maybe that was part of it??

Here is the reply from the last command you sent me to use.
j```
eromy@itronix:~$ grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Power Button"
N: Name="Sleep Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="ImExPS/2 Generic Explorer Mouse"
N: Name="Dell Dell USB Keyboard"
N: Name="Logitech Optical USB Mouse"
N: Name="No brand 2Port KVMSwicther"
jeromy@itronix:~$ 
```

Also for the xinput --list it has added this to it now.
```
"Wacom Serial Tablet PC Pen Tablet/Digitizer"    id=7    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 36
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 17300
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 13000
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
```

I'm on the right path I think.   Thank you so much so far!!

---

### Post by Favux on 2010-02-15
Good!  It's definitely in xinput now.  We should be able to fix the rest but please clear some stuff up for me.

Do the usb grep wacom command.  And what version of linuxwacom did you install with that wiki?  Was it version 0.8.4-4?

---

### Post by jlarmour on 2010-02-15
When I do the command nothing returns.

```
jeromy@itronix:~$ lsusb | grep [Ww]acom
jeromy@itronix:~$ 

```
with the wiki I installed linuxwacom-0.8.5.10  (I used the wiki to follow the code, with the newer driver instead of the 8.1-6)

---

### Post by Favux on 2010-02-15
Ouch!  0.8.4-4 would probably have been a better choice.

You have no wacom.ko, the usb kernel driver/module, and so no usb communication but the tablet works so it must be a serial tablet.

Either of the two .fdi's attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") should get wacomcpl working for you.  See instuctions in Section 2 b).  Then set up wacomcpl using Section 3).  Then you should be able to configure your stylus button and calibrate.

Good luck!

---

### Post by jlarmour on 2010-02-15
Awesome!

Thank you so much for all your help!

J

---

### Post by jlarmour on 2010-02-16
Well, no luck I cannot start  wacomcpl.
I get error message:
[FONT=monospace]
[/FONT]```
jeromy@itronix:~$ wacomcpl
wacomcpl: using TCLLIBPATH="
[list  /usr/local/lib ]"
Error in startup script: xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1953)
jeromy@itronix:~$ 
```[FONT=monospace]

The idf file has been switched, followed the steps in the [/FONT][HOW TO:  Install a LinuxWacom Kernel Driver for Tablet PC's.]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

---

### Post by Favux on 2010-02-16
Hi jlarmour,

It's looking like you didn't install some of the needed libraries/dependencies before compiling linuxwacom.  What does:
```
xinput -list
```
look like now?  And:
```
xsetwacom list
```

---

### Post by jlarmour on 2010-02-16
xinput -list=
```
jeromy@itronix:~$ xinput -list
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
"stylus"    id=2    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 17300
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 13000
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"cursor"    id=3    [XExtensionKeyboard]
    Type is Wacom Cursor
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 17300
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 13000
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -900
        Max_value is 899
        Resolution is 1
    Axis 4 :
        Min_value is -1023
        Max_value is 1023
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"eraser"    id=4    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 17300
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 13000
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Sleep Button"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=8    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=11    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=12    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
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
"ImExPS/2 Generic Explorer Mouse"    id=14    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 13
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
"Logitech Optical USB Mouse"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 7
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
"HID 04f3:0801"    id=10    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 13
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
"HID 04f3:0801"    id=13    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
jeromy@itronix:~$ 
```

xsetwacom list=

```
jeromy@itronix:~$ xsetwacom list
xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
jeromy@itronix:~$
```

---

### Post by Favux on 2010-02-16
OK, it's probably too late but let's try this anyway.  If you look at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") you'll see this in Step 2:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade
```
Go ahead and run (copy & paste and then enter) those commands in a terminal.  Make sure you get all of the middle command.  Then reboot and see what happens.

Never tried it after the fact before.  Did you see a bunch of errors compiling?  But it still finished and let you do "sudo make install"?  Fingers crossed.

---

### Post by jlarmour on 2010-02-16
```
Reading state information... Done
build-essential is already the newest version.
libx11-dev is already the newest version.
libxi-dev is already the newest version.
x11proto-input-dev is already the newest version.
xserver-xorg-dev is already the newest version.
tk8.4-dev is already the newest version.
tcl8.4-dev is already the newest version.
libncurses5-dev is already the newest version.
```

```
jeromy@itronix:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeromy@itronix:~$ 
```


no luck it looks like on that says already installed, I'll reboot.

---

