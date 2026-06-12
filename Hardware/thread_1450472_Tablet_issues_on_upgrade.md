---
title: "Tablet issues on upgrade"
date: 2010-04-09
forum: Hardware
---

### Post by 213736 on 2010-04-09
I know this topic has been beaten to a pulp and back again, but here's where I'm at. I've got an older Asus R1F( very similar to the R1E, same tablet hardware I believe), USB connected Wacom screen, no touch. I was originally running 8.04 on the system, and based on this [[https://help.ubuntu.com/community/AsusR1E](https://help.ubuntu.com/community/AsusR1E)] guide, I was able to get the screen working flawlessly, better than it was under Windows. Now, the laptop fell out of use (read: got old and I got a new one) but I recently fixed the power cord, and was planning on using this as a mobile desktop of sorts. So I do the logical thing and upgrade, to 9.10 Karmic. The problem is that between my original small pile of skill working with ubuntu and the time it's been since I've dealt with the tablet at all, I've completely gotten lost in all of the stuff. I've followed (or attempted to, at least) both [[http://ubuntuforums.org/showthread.php?t=1038949&highlight=asus+r1f+tablet+9.10](http://ubuntuforums.org/showthread.php?t=1038949&highlight=asus+r1f+tablet+9.10)] and [[http://ubuntuforums.org/showpost.php?p=7093065&postcount=104](http://ubuntuforums.org/showpost.php?p=7093065&postcount=104)], to no avail. The problems start when I go to upgrade the system (step 2 on the gali98 walkthru), and enter this:

```

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

```I end up with the system telling me to insert the install CD into /cdrom/, even tho it is already in the drive. Continuing from there, seeing as the system is, in fact, up to date, after I get to:

```
sudo ./configure --disable-quirk-tablet-rescale --enable-wacom
```and go to make, it can't find a make file. This seems to be unique to something I'm doing wrong, otherwise I feel it would have been corrected in the tutorial by now (note, the --disable-quirk-tablet-rescale is something from the original setup that seemed to work, and I've run both with and without to no avail) . The config log I've attached to this post is what I was fed out (had to post it as a .doc because the .txt was too large). My worst case scenario is simply to go back to a new install of 8.04, which would be a shame because 9.10 seems to run smoother and load faster , not to mention it looks a good deal slicker too. Any help would be greatly appreciated, and I'll provide any information requested that will help. 

One last thing, this is the readout I get from 'xinput --list':

```

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
"Power Button"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Asus Laptop extra buttons"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=8    [XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"    id=9    [XExtensionPointer]
    Type is TOUCHPAD
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

```I'm assuming that the "Virtual pointer" is the tablet, but I'm not sure on that one either. Again, any help appreciated, and thanks in advance

---

### Post by 213736 on 2010-04-10
Forgot to mention, this is the lsusb output

```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 114: ID 056a:0090 Wacom Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

so it is, at least, seeing the tablet on the system.

---

### Post by 213736 on 2010-04-11
Shameless bump, would really like to get some help with this if it's possible

---

### Post by Favux on 2010-04-14
Hi 213736,

Did you try the new-generic .fdi at the bottom of the linuxwacom How To?  Instructions in 2 b).  What versions of linuxwacom are you compiling?  The default package for Karmic, 0.8.4-1 should work fine for you.  On your configure flags you'll also want "--prefix=/usr".

---

### Post by 213736 on 2010-04-14
I've been compiling version 0.8.4-4, which is the closest version to the one specified by the USB one posted. The -1 version isn't up for download on the linuxwacom site, so if I need to go back to that version, and it came with the distro, I guess I could get it off the install cd? Not sure about that. The .fdi I had been using was the one that gali98 specified for their system, but I pulled out the touch part that I don't need and used calibration numbers from the last time I set up, on 8.04 with Xorg. I'll try to clean the system of the wacom work I've done and reconfigure/make with the --prefix=/usr and the generic .fdi, and see how that goes

edit: used ./uninstall in the directory, then did 

```
 ./configure --enable-wacom --prefix=/usr

make

sudo cp ./src/2.6.31/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```and used the generic .fdi file, but no dice on that one either.

Should probably mention that I'm on kernel 2.6.31-20-generic right now. 
Also
```

philip@Ringworld-Dock-013:~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2010-04-14 10:46 platform-i8042-serio-0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 9 2010-04-14 10:46 platform-i8042-serio-4-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2010-04-14 10:46 platform-i8042-serio-4-mouse -> ../mouse1
philip@Ringworld-Dock-013:~$ dmesg | grep Wacom
[   15.585163] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver

```

Not sure if any of that helps or not.

---

### Post by Favux on 2010-04-14
Hi 213736,

Since the tablet isn't showing up in the xinput let's see if the linuxwacom usb kernel driver is auto-loading for you.  In a terminal:
```
lsmod | grep wacom
```

---

### Post by 213736 on 2010-04-14
Here's what I got for ya

```

philip@Ringworld-Dock-013:~$ lsmod | grep wacom
wacom                  22052  0 

```

---

### Post by Favux on 2010-04-14
Ok, so wacom.ko is loading.  Does your digitizer show up in 'xinput --list' since you recompiled?

---

### Post by 213736 on 2010-04-14
Hmm, not from what I'm seeing, unless it's identified as something else 

```

philip@Ringworld-Dock-013:~$ xinput --list
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
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Asus Laptop extra buttons"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=8    [XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"    id=9    [XExtensionPointer]
    Type is TOUCHPAD
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


Edit: I thought I'd mentioned it in this thread, but apparently not. I did get it to work once, properly, after I rebooted it picked up, and with the calibration numbers I had it followed 1:1, but I didn't get a chance to test pressure sensitivity or anything else really, because once I rotated the screen, all support ended, and I haven't seen it since. That was using 0.8.4-4 and my modified calibration off of the gali98 .fdi. I do have the wacom calibration autoload program setup and activated right now, and that's all that I can think of off the top of my head right now.

---

### Post by Favux on 2010-04-14
This isn't making a lot of sense.  Don't see it unless it's one of the keyboards.  Let's look at your lshal:
```
lshal>213736_lshal.txt
```
Right click on it and use Create Archive to compress it and use Manage attachment below to attach it to your next post.

---

### Post by 213736 on 2010-04-14
Alright, here you go. Hopefully you can make more sense of it than I can

---

### Post by Favux on 2010-04-17
OK, the lshal output shows HAL knows you have a tablet pc.  But there is no indication of a Wacom digitizer.

To rule out hardware failure does the digitizer work in Windows or whatever?

As far as I know there should be an internal usb connection.  See: [https://help.ubuntu.com/community/AsusR1E](https://help.ubuntu.com/community/AsusR1E)  Maybe it's loose at the motherboard?

Also lshal indicates a dock.  Are you doing all this with your tablet in a docking station?

---

