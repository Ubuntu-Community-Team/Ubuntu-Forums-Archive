---
title: "used howto: webcam not working still"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by CarbonPlexus on 2005-11-25
Alright I used the HOWTO for Logitech USB webcams found at
[HOWTO: logitech, labtec webcams with qc-usb driver]("http://www.ubuntuforums.org/showthread.php?p=520558")

I got through part of the installer and then it said:

> Now I finally will try to load the module.
If you're unlucky, your computer might crash right now!!!!
Consider long if you really want to continue.
Press Ctrl+C to quit, Enter to continue --->

You decided to do it, here we go...
=== Leaving root mode ===
The driver detected the following supported cameras:
[!] No cameras detected.
Try unloading and reloading the driver manually with
        rmmod quickcam; insmod ./quickcam.ko debug=-1
and then checking whether there are any messages indicating
problems with command
        dmesg
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.

so then I tried the 2 commands it showed

> k---@M-------:~/Desktop/qc-usb-0.6.3$ rmmod quickcam; insmod ./quickcam.ko debug=-1
insmod: error inserting './quickcam.ko': -1 Operation not permitted
k---@M-------:~/Desktop/qc-usb-0.6.3$ dmesg
[4297560.236000] usbcore: registered new driver quickcam
[4297576.374000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297576.374000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297576.462000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297576.462000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297699.500000] usbcore: deregistering driver quickcam


Any idea what this is about?  I have a Logitech Quickcam Messenger but I got the special driver for it that was moddified from the other Logitech webcams because it's supposed to be slightly different.  Also I see a camera in the Device Manager so it shows up but it's not registering with the driver :confused:  Any thoughts/help would be appreciated ^_^ *I'm really new at installing drivers so am I doing something that's obviously wrong?  Everything else before that seemed to install correctly with no errors other than the webcam just won't be detected*

---

### Post by teaker1s on 2005-11-25
setkeycodes is the button on webcam that kernel doesn't know  look at wilki and seach multimedia select multimedia keys and follow the howto
I've the same webcam but I haven't tried howto yet

---

### Post by CarbonPlexus on 2005-11-26
I couldn't get through the howto because once I got to the third part 'Assigning X keysyms' where you open a terminal and type > xev and then push the 'multimedia key' which is supposed to be the button on top of the cam nothing outputs to the terminal, like it doesn't exist.

And I still don't have any webcam picture/video which is the part I care the most about since I don't really use the key on top anyway but I tried it because I thought if that worked then maybe I could at least get photos even though the video doesn't seem to be working :???:

---

