---
title: "Intel Classmate: touchscreen acts like touchpad"
date: 2010-01-09
forum: Hardware
---

### Post by mooware on 2010-01-09
Hi there!

I recently installed Karmic UNR on my Intel Classmate Convertible, and interestingly the touchscreen immediately worked partially. But it doesn't act like a touchscreen. I can't click at all, and when I move the stylus on the screen, the cursor only moves relative to its position, like using a touchpad.
This behaviour is especially strange because when I first tried to install the Karmic netbook remix on the same hardware, I could only click, but not move the cursor.
I tried instructions from [here]("http://www.admindu.de/wordpress/?p=453") and [here]("http://ubuntuforums.org/showthread.php?t=1182225") to make the touchscreen work, but that didn't change anything.

In the Xorg log i found the following segment. eTurboTouch is the manufacturer of my touchscreen, so maybe it already is the right driver, but I don't know how to configure it.

```
(II) config/hal: Adding input device eTurboTouch eTurboTouch
(**) eTurboTouch eTurboTouch: always reports core events
(**) eTurboTouch eTurboTouch: Device: "/dev/input/event7"
(II) eTurboTouch eTurboTouch: Found 3 mouse buttons
(II) eTurboTouch eTurboTouch: Found x and y absolute axes
(II) eTurboTouch eTurboTouch: Found absolute touchpad
(II) eTurboTouch eTurboTouch: Configuring as touchpad
(**) eTurboTouch eTurboTouch: YAxisMapping: buttons 4 and 5
(**) eTurboTouch eTurboTouch: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "eTurboTouch eTurboTouch" (type: TOUCHPAD)
(**) eTurboTouch eTurboTouch: (accel) keeping acceleration scheme 1
(**) eTurboTouch eTurboTouch: (accel) filter chain progression: 2.00
(**) eTurboTouch eTurboTouch: (accel) filter stage 0: 20.00 ms
(**) eTurboTouch eTurboTouch: (accel) set acceleration profile 0
(II) eTurboTouch eTurboTouch: initialized for absolute axes.
```How can I reconfigure or at least remove the mentioned device, so that maybe one of the guides above would work?

Any help is appreciated.

EDIT:
Looks like reinstalling Ubuntu doesn't really remove the old stuff. I did a fresh install on a new SD Card and now it's the way it should be according to the guides mentioned above. But I still can't get the touchscreen to work.

EDIT 2:
Got it working now, great stuff!

---

### Post by nam31355 on 2010-02-14
Hi there! It's my first post in this forum.. In fact, it's my third day using Ubuntu Netbook Remix (Karmic Koala 9.10) on an Intel powered Classmate Convertible PC.. I am pretty excited about it, but also pretty confused trying to get everything to work, reading lots of new stuff and gathering millions of pieces of information about this new (for me) OS, which I find really interesting!

So, just like you, I have the eTurboTouch Touch Screen which works only partially (it moves the mouse, but not correctly calibrated, and it doesn't click at all)..

I visited [www.eturbotouch.com](www.eturbotouch.com) and downloaded drivers for CB-R400 and CB-R500, for Ubuntu 9.04 (there is nothing for Ubuntu 9.10).. Was that what I was supposed to do? I hope I didn't download the wrong drivers..

Then, I copied xfhiddrv_drv.so to /usr/lib/xorg/modules/input, as explained in the Readme..

Now, I am supposed to edit /etc/X11/xorg.conf, and add the following lines:

Section "InputDevice" 
    Identifier  "HID TOUCH" 
    Driver      "xfhiddrv" 
    Option      "Device" "/dev/usb/hiddev0" 
    Option      "ScreenNo" "0" 
    Option      "Rotation" "0" 
    Option      "SwapY" "0" 
    Option      "UpSound" "0" 
    Option      "DownSound" "0" 
EndSection

However, there is no xorg.conf in 9.10! Reading other posts, I found out that this is a modification made in 9.10.. However, I read that if you create a xorg.conf including your settings, it is going to be used as in older versions.. So, I made an empty xorg.conf and copied the above lines, rebooted the PC, but nothing happened.. Furthermore, I tried using the xorg.conf files from the links that you provide in the above.. But nothing happened again..

How did you make your touchscreen work?

P.S. Please take into account that, even if I am a good learner, I am still a newbie, so please try to explain as much as you can..

Thanx in advance!

---

### Post by mooware on 2010-02-15
Hi. It has already been some time since I set my classmate up and I'm not a linux expert either, but I'll try to help you with what I know. Let's see...

I'm not sure which of the drivers you name is the right one, I just downloaded the one that was used in the article I mentioned ([http://www.eturbotouch.com/dimage/driver_n/20095181249115.zip](http://www.eturbotouch.com/dimage/driver_n/20095181249115.zip)).

The empty xorg.conf is probably also a problem, since it will miss the ServerLayout-section and other stuff which might be important. I believe I used dexconf, which takes your current configuration and writes a new configuration file with it. Since you also have a Classmate Convertible, you can probably just use my xorg.conf:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
  InputDevice    "HID TOUCH" "SendCoreEvents"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dbe"
    Load  "dri"
    Load  "extmod"
    Load  "glx"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice"
        Identifier  "HID TOUCH"
        Driver      "xfhiddrv"
        Option      "Device" "/dev/usb/hiddev0"
        Option      "ScreenNo" "0"
        Option      "Rotation" "0"
        Option      "SwapY" "0"
        Option      "UpSound" "0"
    Option      "DownSound" "0"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 945GME Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

That should get the touchscreen to work. But it doesn't give you automatic screen rotation when you turn the screen. I followed the instructions from [http://www.admindu.de/wordpress/?p=453](http://www.admindu.de/wordpress/?p=453) to get that to work, now the image rotates, but the touchscreen doesn't rotate with it. I set the touchscreen rotation in the xorg.conf so that it fits for tablet mode.

---

### Post by nam31355 on 2010-02-15
Thank you very much for your reply!

However, it didn't improve things.. Before you answered, I managed to create a new xorg.conf myself, using:
sudo service gdm stop
sudo Xorg -configure
from another terminal (Ctrl+Alt+F2). A xorg.conf.new was created in my home folder, which I renamed and moved to /etc/X11 (sudo mv xorg.conf.new /etc/X11/xorg.conf). 

After editing this file, it looked pretty much like the xorg.conf that you just posted. Of course, I tried using your xorg.conf, just to make sure, but this didn't work either.

The driver I am using (xfhiddrv_drv.so) is the same one that you are using (the one from the link you posted), and I have copied it to /usr/lib/xorg/modules/input, as I suppose that you did, as well. So, I guess there must be something else.. but what???

Just in case, what version of Xorg are you using? As I saw in my xorg log (var/log/xorg.0.log), I have:

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 

Somewhere in xorg log I found out these lines:

(II) LoadModule: "xfhiddrv"
(II) Loading /usr/lib/xorg/modules//xfhiddrv_drv.so
(II) Module xfhiddrv: vendor="CSWU, Risintech"
    compiled for 1.6.0, module version = 1.2.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0

So, is it possible that the problem is that xfhiddrv is compiled for Xorg 1.6.0 and I am using Xorg 1.6.4? Could there be any sort of incompatibility?

Do you have any other suggestions?
Do you remember doing something else to make the touchscreen work?

Thank you very much once again!

---

### Post by mooware on 2010-02-17
Here is the top of my Xorg.0.log:

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mooware-classmate 2.6.31-14-cmpc #48 SMP Wed Nov 18 15:03:51 CET 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-cmpc root=UUID=58e58f5c-bcfb-4e7e-8d0d-091a1f488f61 ro splash quiet quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 

```Looks quite like yours, except for the patched kernel I'm using. But I am certain that the touchscreen already worked before I installed the custom kernel, which enables screen rotation and adjusting screen brightness.

Here's the part of my log about the driver:

```
(II) LoadModule: "xfhiddrv"
(II) Loading /usr/lib/xorg/modules/input//xfhiddrv_drv.so
(II) Module xfhiddrv: vendor="CSWU, Risintech"
            compiled for 1.6.0, module version = 1.2.0
            Module class: X.Org XInput Driver
            ABI class: X.Org XInput Driver, version 4.0
```The path to the driver is different from yours, but it shows information about the driver, so I guess it loads correctly.

I also found the following part in the log, but I am sure that this part was there even before I installed the driver, although its contents may have changed.

```
(II) config/hal: Adding input device eTurboTouch eTurboTouch
(**) eTurboTouch eTurboTouch: always reports core events
(**) eTurboTouch eTurboTouch: Device: "/dev/input/event7"
(II) eTurboTouch eTurboTouch: Found 3 mouse buttons
(II) eTurboTouch eTurboTouch: Found x and y absolute axes
(II) eTurboTouch eTurboTouch: Found absolute touchpad
(II) eTurboTouch eTurboTouch: Configuring as touchpad
(**) eTurboTouch eTurboTouch: YAxisMapping: buttons 4 and 5
(**) eTurboTouch eTurboTouch: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "eTurboTouch eTurboTouch" (type: TOUCHPAD)
(**) eTurboTouch eTurboTouch: (accel) keeping acceleration scheme 1
(**) eTurboTouch eTurboTouch: (accel) filter chain progression: 2.00
(**) eTurboTouch eTurboTouch: (accel) filter stage 0: 20.00 ms
(**) eTurboTouch eTurboTouch: (accel) set acceleration profile 0
(II) eTurboTouch eTurboTouch: initialized for absolute axes.
```The following part of the log seems to mirror what I configured in the xorg.conf file.

```
(**) priv->input_dev: /dev/usb/hiddev0
(**) HID Touch HID TOUCH input device: /dev/usb/hiddev0
(**) Option "SendCoreEvents"
(**) HID TOUCH: always reports core events
(**) Option "ScreenNo" "0"
(**) Option "Rotation" "0"
(**) Option "DownSound" "0"
(**) Option "UpSound" "0"
(**) Option "SwapY" "0"
(II) XINPUT: Adding extended input device "HID TOUCH" (type: Touch Screen)
(**) Find device : /dev/usb/hiddev0
(**) Option "Device" "/dev/usb/hiddev0"
```Just like you, I had to tinker a lot with the device until I got the touchscreen working, but I can't remember what I did to finally get it running.

---

### Post by nam31355 on 2010-02-17
Seems like our Xorg logs are the same as well... Which means:
- same netbook
- same os
- same drivers
- same xorg.conf
- same xorg logs

There definitely must be something else..

Anyway, thank you really much for your help and for your time.. If you remember anything further, you'll be most helpful! ;)

P.S. Could you please change the [solved] thing, so that maybe someone else replies in the thread?

---

### Post by nam31355 on 2010-02-18
Could it be the fact that I have installed UNR using WUBI?

---

### Post by mooware on 2010-02-18
Well, I installed from a USB stick with the standard UNR cd image, prepared with [Unetbootin]("http://unetbootin.sourceforge.net/"). So that's one thing our setups don't have in common. But I don't think that it makes that much of a difference.

You wrote before that you can move the cursor, but you can't click. That's how it was for me through several reinstallations, but actually it should be the other way around. In the first and the final setup, I was only able to click, but the cursor didn't move. So maybe you should try a fresh install (not just installing over the old data).

---

### Post by nam31355 on 2010-02-19
I did a fresh install, from a USB stick, using Unetbootin, just like you did.. But it didn't make the touch screen work.. Anyway, I think I'm going to give up.. Disappointing, though, for a first experience with linux.. :(

---

