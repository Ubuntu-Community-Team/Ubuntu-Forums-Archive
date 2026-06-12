---
title: "[SOLVED] Logitech Cordless Desktop s510 // Gutsy"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by hebetude on 2007-11-11
s510 buttons: Zoom +/-, 100%, rotate, shuffle, 

I got this keyboard, but all matter of beating it against my head hasn't made the "extra" buttons work.  They apparently use keycodes out of the normal range for linux <255.  So, what is there to do about this?

There's a kernel patch, but this keyboard has been specifically added to the kernel.

[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.21](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.21)
> commit b55fd23ccdf32f969a7b4180c6e52d62d8e99972
Author: Jiri Kosina <jkosina@suse.cz>
Date:   Wed Feb 21 19:27:49 2007 +0100

    HID: fix broken Logitech S510 keyboard report descriptor; make extra keys work
    
    This patch makes extra keys (F1-F12 in special mode, zooming, rotate, shuffle)
    on Logitech S510 keyboard work.
    
    Logitech S510 keyboard sends in report no. 3 keys which are far above the
    logical maximum described in descriptor for given report.
    
    This patch introduces a HID quirk for this wireless USB receiver/keyboard
    in order to fix the report descriptor before it's being parsed - the logical
    maximum and the number of usages is bumped up to 0x104d). The values are in the
    "Reserved" area of consumer HUT, so HID_MAX_USAGE had to be changed too.
    
    In addition to proper extracting of  the values from report descriptor, proper
    HID-input mapping is introduced for them.
        Signed-off-by: Jiri Kosina <jkosina@suse.cz>Built from bug [7352.]("http://bugzilla.kernel.org/show_bug.cgi?id=7352")

However, these buttons still don't work.  I use Gutsy, kernel version 2.6.22-14-generic.  So, these additions should be in my kernel.  Someone stated that the options merely need to be activated by adding the following to /etc/modprobe.d/options

```

options usbhid quirks=0x46d:0xc517:0x100000 
```However, xev still doesn't register events for the extra buttons.  Is this a simple arrangement, clearly the change log for the kernel isn't helping since it doesn't mention anything about having to add quirk options to turn on these "included" features.

Thanks,

---

### Post by hebetude on 2007-11-18
I have not attempted to map this keys, but xev picks up every key now.  Even F1-F12 and the secondary set F1-F8 + abcd as independent keys.

Find the magic cure at:
[http://ubuntuforums.org/showpost.php?p=3794702&postcount=14](http://ubuntuforums.org/showpost.php?p=3794702&postcount=14)

Basically do this:
add a line to /etc/modprobe.d/options
```

options usbhid quirks=0x46d:0xc517:0x100000
```

Now you need to switch to the evdev driver on both the mouse/keyboard and to link to their respective devices keyboard=event1 and mouse=event2.  I've included my Xorg configuration file:

```

Section "ServerLayout"
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Logitech s510 Keyboard"
    InputDevice    "Logitech s510 Mouse"  "SendCoreEvents"
    Option        "AIGLX" "true"
EndSection

Section "InputDevice"
    Identifier  "Logitech s510 Keyboard"
#    Driver      "kbd"
    Driver      "evdev"
    Option      "Device"    "/dev/input/event1"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "evdev"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Logitech s510 Mouse"
#    Driver      "mouse"
    Driver      "evdev"
    Option        "Device"    "/dev/input/event2"
    Option      "SendCoreEvents"   "true"
        Option      "Name" "Logitech USB Receiver"
        Option      "Resolution" "800"
#    Option        "CorePointer"
#    Option        "Device" "/dev/input/mice"
#    Option        "Protocol" "ImPS/2"
#    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "false"
EndSection


```

I merely commented out some of the default things Xorg-reconfigure wrote in there, so that you can use it for comparison.  Props to [minimec]("http://ubuntuforums.org/search.php?searchid=31538758") for cracking this forgotten nut.

I'm off to figure out what I want to do with these new 17 keys.

---

### Post by floquet on 2008-01-16
This will work for me only if I add to the mouse configuration in the Xorg.conf

```
Option     "CorePointer"
```

Regards

---

### Post by chenel on 2008-04-29
When I applied the quirk and switched to the evdev driver, my mouse would only move the pointer up and down on the screen...

Any ideas?

---

### Post by njbair on 2008-05-03
Did you ever figure out why the mouse only moves up and down? I have the same trouble.

---

### Post by chenel on 2008-05-03
No, I just went back to the regular keyboard and mouse drivers.  I haven't really had time to play with it that much, and I don't *need* all those extra keys anyway.  Maybe I'll play with it some more in the future -- if I figure it out I'll post here.

---

