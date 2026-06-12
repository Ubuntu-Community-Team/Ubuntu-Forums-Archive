---
title: "Cannot click icons when using pen on my Fujitsu t730 tablet"
date: 2013-11-22
forum: Hardware
---

### Post by zottelmann on 2013-11-22
Hello!

I hope you guys/girls can help me here. As stated above i'm using a FS t730 Lifebook. Everything runs smoothly, but when i use my digitizer, after some time im not able to use the UI anymore. On Xournal i still can wirte one the paper, but any icon on the interface or the system do not work anymore. The solution is to relog, which is not very comfortable in my opinion. the problem exists on 13.04 and 13.10. i didnt tested it on 12.xx.
I use the lifebook for writing in my classes. So its important for me to get it working.
Any sugestions?
Thanks alot!

---

### Post by Favux on 2013-11-22
Hi zottelmann,

What you are describing does not make much sense.  A log out and in is kind of a hotplug I guess.

I assume the t730 has a Wacom digitizer?  Post the output of **xinput list** in a terminal to check.

The no left click would probably occur if a Wacom active pen/digitizer was on the evdev X driver instead of the Wacom X driver.  But I do not see how that could happen if the 50-wacom.conf in xorg.conf.d matches to the digitizer to begin with.  Your Xorg.0.log in /var/log would tell you what driver it is on and if it switched drivers.  But the connection to the digitizer from the motherboard should be internal.  If the connection was loose and it essentially performed a hotplug the wacom.conf should still match it to the Wacom X driver, i.e. take it away from the evdev X driver.

You don't state what Desktop you are using in 13.04 or 13.10.  Maybe the problem is the Desktop?  If Unity perhaps some bug is causing it to become unresponsive which is fixed with a log out and in.

---

### Post by zottelmann on 2013-11-23
Hi Favux!
Sorry for the delay :)
I'm using indeed Unity

this is my xinput:
```

Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=18    [slave  pointer  (2)]

```



And here's the log(only looking for stylus):
```

[    23.687] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    23.687] (II) Serial Wacom Tablet: other types will be automatically added.
[    24.198] (II) Serial Wacom Tablet stylus: serial tablet id 0xE3.
[    24.198] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    24.199] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    24.199] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    24.199] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[    24.199] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[    24.199] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    24.199] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0b/tty/ttyS4"
[    24.199] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 16)
[    24.199] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[    24.199] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[    24.199] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[    24.199] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4

```

Many thanks for your help!

Zottel

---

### Post by Favux on 2013-11-23
Alright, Unity and your **xinput list** shows the Wacom digitizer/stylus is on the Wacom X driver because we see stylus, eraser, and touch appended to the parent device name of "Serial Wacom Tablet".

The key line in Xorg.0.log is:
```
[    24.199] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 16)
```
That tells us the digitizer has been successfully hot plugged onto a X driver.  Above the part you showed would be a line(s) with snippet identifier labels in them.  The Identifier is a line added to each .conf file "InputClass" snippet in xorg.conf.d to produce a human readable label for the snippet in the logs.  The last line you see is the snippet in charge.  In this case it should have said something like "Wacom serial class".  Which tells you that snippet is trying to match the device to the Wacom X driver.

If further down in Xorg.0.log you suddenly see the device going through another hotplug but this time it is identified as an evdev snippet from the evdev.conf that would explain what you are seeing.  But since it matches the Wacom snippet the first time why wouldn't it match it again?  So I really doubt this is the problem.

It could be a problem with Unity I suppose.  But the early problems with Compiz are pretty much gone at this point.  Besides I gather your other pointing devices, a trackpad and/or mouse are still doing left clicks, so it isn't a general pointer issue.

I wonder if this is a hardware problem.  The stylus may be going bad.  I can't recall but I think tablet PC styli have replaceable nibs too.  Have you tried extracting and replacing the nib (tip) of your stylus and checked if that made a difference?  The nib has to be about 4 years old or some such If it has never been replaced.  An extractor tool and replacement nibs should have been included.

---

### Post by zottelmann on 2013-11-23
Wow, you seem to have an awesome insight to Ubuntu :)

I'm sorry i forgot to tell, that only Keyboard is working when the bug happens. Left/right clicking doesn't on the other devices. But there another thing i discovered, when i looked closer to my stylus to see how the nib was surviving: i saw a little "HP" logo. So if this is not the original Stylus, can it cause so much trouble to Xinput? To explain: the Lifebook is a refurbished Model from Ebay from a private seller. Maybe it was mixed up or something.

Windows on the other hand works well, even with wrong stylus as i now know. But i dont want to use it ;)

---

### Post by Favux on 2013-11-23
Well there is a difference between pens/styli and they will only work on "their" model Wacom digitizer.  But tablet PC styli are most likely interchangeable because their digitizers are pretty much of the same type.  The fact that it does work, at least initially, suggests the HP pen is compatible with the Thinkpad's digitizer.
> only Keyboard is working when the bug happens. Left/right clicking doesn't on the other devices.
That suggests to me that you do have some sort of system bug.  Most likely with Unity.  Something is probably crashing.  That may be in your Xorg.0.log too.  Open it in gedit and use Find with keywords like error, crash, seg fault, and so on.  It might be a video driver problem I suppose.  What video chipset do you have?
```
lspci | grep VGA
```

---

### Post by zottelmann on 2013-11-23
Hi!

Thank you for hanging on ;)
lspci tells this:
```
 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

On the paper the t730 has a intel i5 560m.

the only thing i found on the logfile was:
```


 5974.091] (II) Failed to load module "intel" (already loaded, 32698)
[  5974.091] (II) LoadModule: "vesa"
[  5974.091] (WW) Warning, couldn't open module vesa
[  5974.091] (II) UnloadModule: "vesa"
[  5974.091] (II) Unloading vesa
[  5974.091] (EE) Failed to load module "vesa" (module does not exist, 0)
[  5974.091] (II) LoadModule: "modesetting"
[  5974.091] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  5974.091] (II) Module modesetting: vendor="X.Org Foundation"
[  5974.091]     compiled for 1.14.1, module version = 0.8.0
[  5974.091]     Module class: X.Org Video Driver
[  5974.091]     ABI class: X.Org Video Driver, version 14.1
[  5974.091] (II) UnloadModule: "modesetting"
[  5974.091] (II) Unloading modesetting
[  5974.091] (II) Failed to load module "modesetting" (already loaded, 0)
[  5974.091] (II) LoadModule: "fbdev"
[  5974.091] (WW) Warning, couldn't open module fbdev
[  5974.091] (II) UnloadModule: "fbdev"
[  5974.091] (II) Unloading fbdev
[  5974.091] (EE) Failed to load module "fbdev" (module does not exist, 0)
[  5974.091] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[  5974.092] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  5974.092] (++) using VT number 7

```

wich suggesting some problems with the graphics?

but later it seems to find something:
```

[  5974.092] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.904-0ubuntu2 (Timo Aaltonen <tjaalton@ubuntu.com>)
[  5974.092] (WW) Falling back to old probe method for modesetting
[  5974.092] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  5974.092] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  5974.093] (==) intel(0): RGB weight 888
[  5974.093] (==) intel(0): Default visual is TrueColor
[  5974.093] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics


```

what does this tell us? :) working as intended?

---

### Post by Favux on 2013-11-23
I'm not a video guru but it does look like there is a problem but it eventually gets sorted out.  I was wondering if you had Nvidia because there has been a real increase in the rate of freezes/crashes with the OSS nouveau drivers.  But if you aren't seeing any problems reported in the log when you lose left click I don't know.  Another source of information would be **dmesg** (in a terminal).  But I don't know what you would grep to find out what is happening.  The output is pretty large.  You'd have to write it to a text file and open that in gedit and then look at it and use Find and guess some key words to see if you can spot something.  So after you lose left click run in a terminal:
```
dmesg > ~/Desktop/dmesg.txt
```
to create the file dmesg.txt on the Desktop.  Presumably the problem should be reported somewhere near the end of the file, which is about a thousand lines long.

---

### Post by zottelmann on 2013-11-25
Hello!

Again my apologies for the delay. I was able to create the Dmsge.txt and there was one thin at the end wich seems to be related to my problems:
```
[ 6770.305704] psmouse serio4: bad data from KBC - bad parity
[ 6770.307619] psmouse serio4: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 6770.312224] psmouse serio4: GlidePoint at isa0060/serio4/input0 - driver resynced.
[ 6770.313560] psmouse serio4: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 6770.315366] psmouse serio4: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 6770.316905] psmouse serio4: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 6770.329534] psmouse serio4: GlidePoint at isa0060/serio4/input0 - driver resynced.
```

But im not sure what it exactly means.

regards

---

### Post by Favux on 2013-11-25
```
[ 6770.305704] psmouse serio4: bad data from KBC - bad parity
```
Likely means the data stream from the mouse is dropping out.  The serio probably refers to a serio kernel module.  That's the new way of handling serial devices.  Instead of an X driver reading them directly off a serial port a serio kernel module reads them and feeds them to the X driver analogous to how a usb device works.

Hmm.  I wonder if your PS/2 mouse, or its connection, is going bad.  Check that the connections are good, especially with the adaptor if it requires one.  Otherwise I'd substitute a usb mouse for it and see if that fixes the problem.

---

### Post by zottelmann on 2013-11-26
Hi,

ummm... i dont use any mouse on this notebook XD just touchpad/stylus/touchscreen. there is also no ps2 connector, but maybe its still a hardware issue. than, on the other hand, it shouldnt work on windows. but it works flawless.

dmsge showed also this conflict, but i dont believe that it has anything to do with my problem(edit: google said its just infomational):
```
[   16.516838] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \_SB_.PCI0.LPCB.PMIO 1 (20130517/utaddress-251)
[   16.516839] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.516844] ACPI Warning: 0x00000000000011b0-0x00000000000011bf SystemIO conflicts with Region \_SB_.PCI0.LPCB.OGIO 1 (20130517/utaddress-251)
[   16.516845] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.516848] ACPI Warning: 0x0000000000001180-0x00000000000011af SystemIO conflicts with Region \_SB_.PCI0.LPCB.OGIO 1 (20130517/utaddress-251)
[   16.516849] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.516894] lpc_ich: Resource conflict(s) found affecting gpio_ich
```

thanks for your patience and help so far :)

---

### Post by Favux on 2013-11-26
I agree with you, I don't think that has anything to do with the no click issue.

From your xinput list:
```
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=18    [slave  pointer  (2)]
```
X seems to think there is a PS/2 serial mouse plugged in:
```
&#9116;   &#8627; PS/2 Mouse                                  id=14    [slave  pointer  (2)]
```
and it isn't the Alps touchpad.  So there appears to be an unaccounted for pointing device.  Something is acting like its left click button gets stuck.  Either the Wacom stylus, the Alps touchpad, or the phantome PS/2 mouse.

Another place to look is in the .xsession.log, a hidden file in your /home/username directory.  I think 13.10 is when they go to gnome-session.log.  That's in the same directory but in the hidden .cache folder, .cache/upstart/gnome-session.log.  It's possible that might show the issue.

But the fact that left click always works in Windows, kind of important information, strongly indicates that it is not a hardware problem.  You buried the headline.  :)

---

### Post by zottelmann on 2013-11-27
Hi,

at the moment the "bug" is not happening this often. just when i want it to happen, nothing happens ;) I'll post the session log, when clicking is gone :)
Oh, and sorry for missing so much details about the problem :)

---

### Post by zottelmann on 2013-11-27
hello again!

the mentioned log file is now about 2.2 mb big and contains mainly just this:

```
onboard:2007): Gdk-CRITICAL **: gdk_device_get_axis_use: assertion 'index_ < device->axes->len' failed
```

sometimes a missing file also, but nothing from the system. its pretty much stuff in there so maybe i find more...

---

### Post by Favux on 2013-11-27
Are you saying this line appears in the log:
> onboard:2007): Gdk-CRITICAL **: gdk_device_get_axis_use: assertion 'index_ < device->axes->len' failed
multiple times, i.e. many, many times in a row?

---

### Post by zottelmann on 2013-11-28
jepp. 2 mb text. just this line over and over again and nearly nothing else

i found out why the "gnomesession.log" is getting so big. im using the "onboard" keyboard when im in tablet mode with my lifebook. clicking a "key" oder move the onscreen keyboard around, causes the mentioned "onboard:2007): Gdk-CRITICAL **: gdk_device_get_axis_use: assertion 'index_ < device->axes->len' failed" line to be added into the logfile. so often that i can watch the size of this logfile rising while dragging the "onboard". is this working as intended? has this anything to do with my initial problem?

---

### Post by Favux on 2013-11-28
I think you may have found the problem.  I should have recognized onboard meant Onboard.  :)

The Onboard on screen keyboard may be it.    Although the complaint is about the the axes that may be what is issuing a "stuck" left click, perhaps the Enter key?

Try using CellWriter instead of Onboard as your on screen keyboard and see what that does.  Plus CellWriter toggles to letter recognition, which is why I use it in preference to Onboard anyway.

---

### Post by zottelmann on 2013-11-28
Thank you very very much! It will take some testing time, but i think i could nail it to "Onboard" - thanks to your help :) I turned Onboard off and will use Cellwriter instead. 
Thank you again!

---

