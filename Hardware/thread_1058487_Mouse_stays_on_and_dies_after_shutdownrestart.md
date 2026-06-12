---
title: "Mouse stays on and dies after shutdown/restart"
date: 2009-02-02
forum: Hardware
---

### Post by xonpathos on 2009-02-02
Hi all,

First, I'm brand new to Ubuntu.  I've used several distros of Linux before, but it's been quite some time.  So please be gentle.  :)

I've found that I have a problem that was first discussed back in 2005.  When I shutdown my computer, my mouse stays on.  The computer is "off", but the mouse is still lit up.  However, I have a slight twist:  when I turn my computer back on, the mouse refuses to work until I unplug it and plug it back in.  I get the same result when restarting.

About the last thing I found was *[this](http://bugzilla.kernel.org/show_bug.cgi?id=5410)* bug report that offers what amounts to a hack of the kernel to make it stop, but that's dated 2007.  Surely a year and a half later we're not still resorting to people compiling their own kernel with an added hack, are we?

Does anyone else know of a better way to resolve this problem?  If it helps, I'm using a Razer Copperhead mouse and a Gigabyte GA-P35-DS3L motherboard.  I'm running Ubuntu 8.10 (Intrepid Ibex, 

Thanks for your help,

Eric

---

### Post by Yashiro on 2009-02-02
The problem lies with your motherboard and mouse.

> So the problem isn't that the kernel fails to shut the computer down
completely; the problem is that the kernel _does_ shut the computer down
completely and then the BIOS goes crazy.


Look at options in your bios pertaining to usb and/or ps/2.
If you can't resolve it try a bios update.
If that fails, write a script to run on boot up that removes and re-adds your mouse/usb.

I had the same issue on an old P3B-F and was fixed with a bios update.

---

### Post by xonpathos on 2009-02-02
Tried the bios update, didn't help.  I suppose I could hack it with a script, but should I really have to?  Other operating systems seem to handle this hardware just fine.  Why can't Linux?

---

### Post by Yashiro on 2009-02-03
Because it sounds like a bug in your bios to do with booting from mouse/acpi/ps2 legacy/usb suspend.

---

### Post by xonpathos on 2009-02-03
If that were the case, why would it not happen indepenent of what OS I'm running?

---

### Post by Yashiro on 2009-02-03
I'm still waiting for the delivery of my crystal ball.

---

### Post by xonpathos on 2009-02-03
> **Yashiro said:**
> I'm still waiting for the delivery of my crystal ball.
That's particularly helpful, thank you.

It is a legitimate question.  I understand that you personally might not have the answer, but assuming that is the case I would prefer you to not respond at all instead of being a smartass.

---

### Post by Yashiro on 2009-02-03
I was joking. I'm just pointing out that I, the only person who has bothered to help, don't have the magical power to work out why your system has this issue.

If you shutdown from Ubuntu, the mouse remains powered?
If you shutdown from a LiveCD the mouse does what?
If you shutdown via Windows the mouse does what?
Can you boot your PC by pressing a button on your mouse or keyboard?

---

### Post by xonpathos on 2009-02-03
> **Yashiro said:**
> I was joking. I'm just pointing out that I, the only person who has bothered to help, don't have the magical power to work out why your system has this issue.

Sorry.  I do appreciate your help.  I'm just a bit touchy about this because I've defended the validity of Linux to a lot of Windows fanboys of late, and this is exactly the sort of thing that I've said doesn't happen anymore.

> 
If you shutdown from Ubuntu, the mouse remains powered?
Yes.  And it also refuses to work (in any OS) after that until it is unplugged and replugged.
> 
If you shutdown from a LiveCD the mouse does what?
Works properly.
> 
If you shutdown via Windows the mouse does what?
Works properly.
> 
Can you boot your PC by pressing a button on your mouse or keyboard?
The motherboard has the capability, but I have it turned off.

I have the following options in my bios:

Power Management:
PME Event Wakeup: Disabled
Power On By Ring: Disabled
Resume by Alarm: Disabled
Power On By Mouse: Disabled
Power On By Keyboard: Disabled

Integrated Peripherals:
USB Controller: Enabled (kills USB completely if disabled, even in OS)
USB 2.0 Controller: Enabled (kills USB completely if disabled, even in OS)
USB Keyboard Support: Enabled (if disabled keyboard doesn't work in bios/grub, doesn't affect mouse behavior)
USB Mouse Support: Disabled (if enabled you can use mouse in bios, which I don't.  doesn't affect mouse behavior)
USB Legacy Storage Detect: Disabled (seems to only affect whether the bios flash utility recognizes USB drives, doesn't affect mouse behavior)

I've got lots of other options, of course, but these are the only ones that appear to have anything remotely to do with the problem at-hand.

I have found a short-term workaround.  My keyboard (Logitech G15) has 2 USB ports on it.  Apparently when the computer is under the control of the BIOS or when it is off, the keyboard doesn't get enough power to keep the mouse on.  So I can connect my mouse through my keyboard and make things "work".  But I still don't like this option as it takes up one of my two convenient USB ports.

---

### Post by Yashiro on 2009-02-03
The result when shutting down from a LiveCD is interesting.

---

### Post by xonpathos on 2009-02-06
Interesting developments...  I wanted to work on this problem a bit, so I plugged the mouse back in the original port.  Now, the mouse seems to turn off as expected, even in the correct port.  However, it still doesn't work after a restart.

I found something interesting though.  Both dmesg and Xorg.0.log identify the mouse as both a mouse *and* a keyboard.

entries in dmesg:
```
[    4.881880] input: Razer Razer Copperhead Laser Mouse as /devices/pci0000:00/0000:00:1a.2/usb3/3-1/3-1:1.0/input/input1
[    4.900116] input,hidraw0: USB HID v1.00 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:1a.2-1
[    4.903115] input: Razer Razer Copperhead Laser Mouse as /devices/pci0000:00/0000:00:1a.2/usb3/3-1/3-1:1.1/input/input2
[    4.916065] input,hidraw1: USB HID v0.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:1a.2-1
```

entries in Xorg.0.log
```
(II) config/hal: Adding input device Razer Razer Copperhead Laser Mouse
(**) Razer Razer Copperhead Laser Mouse: always reports core events
(**) Razer Razer Copperhead Laser Mouse: Device: "/dev/input/event2"
(II) Razer Razer Copperhead Laser Mouse: Found keys
(II) Razer Razer Copperhead Laser Mouse: Configuring as keyboard
(II) XINPUT: Adding extended input device "Razer Razer Copperhead Laser Mouse" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Razer Razer Copperhead Laser Mouse: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Razer Razer Copperhead Laser Mouse: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Razer Razer Copperhead Laser Mouse: xkb_layout: "us"
(II) config/hal: Adding input device Razer Razer Copperhead Laser Mouse
(**) Razer Razer Copperhead Laser Mouse: always reports core events
(**) Razer Razer Copperhead Laser Mouse: Device: "/dev/input/event1"
(II) Razer Razer Copperhead Laser Mouse: Found x and y relative axes
(II) Razer Razer Copperhead Laser Mouse: Found 8 mouse buttons
(II) Razer Razer Copperhead Laser Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Razer Razer Copperhead Laser Mouse" (type: MOUSE)
(**) Razer Razer Copperhead Laser Mouse: YAxisMapping: buttons 4 and 5
(**) Razer Razer Copperhead Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
```

Is this expected behavior?  Could it be related?

---

### Post by Yashiro on 2009-02-07
That's not normal and may be related to the non function.

Did you paste up your xorg.conf here yet?

---

### Post by xonpathos on 2009-02-07
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "RDS RadiusRad-5"
    HorizSync       30.0 - 63.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "RDS RadiusRad-5"
    HorizSync       30.0 - 63.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1024+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

I have now :)

---

### Post by Yashiro on 2009-02-10
Is this of any use?

[http://ubuntuforums.org/showthread.php?t=1061810](http://ubuntuforums.org/showthread.php?t=1061810)

---

### Post by xonpathos on 2009-02-10
Doesn't sound like it to me.  That seems like it would make the suspend&resume work just like the restart does, which is what isn't working for me.  I've opened a bug at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/327037](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/327037).  I'm not sure Xorg is the right place for it, but that's where I got assigned, so we'll start out there.

---

### Post by xonpathos on 2009-02-10
Well, after some searching I finally found, buried in the depths of the depths of the bug tracker, a half-fix.  Seems that if you update the firmware on the mouse it starts working properly as far as coming back to life after a shutdown/restart.  I still can't get around how it works in Windows and not in Linux, but whatever.

However, I'm holding the bug report open for now because everything is still recognizing it as both a keyboard and mouse.

---

