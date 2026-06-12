---
title: "Trust/Waltop Flex tablet pen no longer moves when hovering"
date: 2011-10-04
forum: Hardware
---

### Post by rosielundberg on 2011-10-04
I bought a Trust Flex (Waltop rebranded) tablet not long ago, and set it up to use with natty on my laptop. I installed the wizardpen driver and, apart from being unable to use the second pen button, the tablet worked fine. Then a few days ago the pen stopped moving when hovering above the tablet; ie, you have to touch pen to tablet to move. I uninstalled and reinstalled the driver to no avail, then tried using the Wacom driver instead, still with no success. Any suggestions as to why this might be happening or how I could fix it?

Thanks :-)

---

### Post by Favux on 2011-10-04
Hi rosielundberg,

Welcome to Ubuntu forums!

It sounds like you have the TabletPCButton "on" and you want it "off" i.e. hover mode.

Let's determine the product ID of your tablet first.  In the output of the:
```
lsusb
```
command in a terminal please post the line that has your tablet in it.  Also post the output of this command:
```
xinput list
```

---

### Post by rosielundberg on 2011-10-04
Here is the output to lsusb:
```

Bus 002 Device 003: ID 172f:0037 Waltop International Corp.

```
And the output to xinput list:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet     eraser    id=16    [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet     pad    id=17    [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet     stylus    id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=15    [slave  keyboard (3)]

```
although i'm guessing it's only the WALTOP entries that are relevant.

thanks :-)

---

### Post by Favux on 2011-10-04
Alright you appear to be on the Wacom X driver because input tool types like stylus, eraser, and pad are being appended.  But because the Waltop lines in *xinput list* i.e. the <device name>'s are a little funky let's double check before trying to use a xsetwacom command.  What is the output in a terminal of this command?:
```
xsetwacom list
```
By the way there is a HOW TO for Waltops:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)

---

### Post by rosielundberg on 2011-10-04
Yes I used the Waltop HOWTO when installing the wacom driver, and followed the instructions for adding the tablet back in (to work round the exception for waltops) but was unable to find a solution for the hover issue.

The command xsetwacom list gives no output...

---

### Post by Favux on 2011-10-04
That makes it sound like the Waltop isn't on the Wacom X driver which is strange given the *xinput list*.  We'll need to look at your Xorg.0.log to figure out what's going on.  It is located in /var/log.  Since it is big you can compress it by right clicking on it and choosing Create Archive.  Then attach it to your next post with Manage Attachments below.

Also post the Waltop line in the output of this command:
```
lsusb
```

---

### Post by rosielundberg on 2011-10-04
Attached is the Xorg.0.log, I posted the output from lsusb in my second post above.

---

### Post by Favux on 2011-10-04
I'm a bit baffled.

It starts out OK:
```
[    27.713] (II) config/udev: Adding input device          WALTOP             Tablet     (/dev/input/event7)
[    27.713] (**)          WALTOP             Tablet    : Applying InputClass "evdev pointer catchall"
[    27.713] (**)          WALTOP             Tablet    : Applying InputClass "evdev tablet catchall"
[    27.714] (**)          WALTOP             Tablet    : Applying InputClass "Waltop on wacom class"
[    27.714] (II) LoadModule: "wacom"
[    27.714] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    27.729] (II) Module wacom: vendor="X.Org Foundation"
[    27.729] 	compiled for 1.10.0, module version = 0.10.11
[    27.729] 	Module class: X.Org XInput Driver
[    27.729] 	ABI class: X.Org XInput driver, version 12.3
[    27.730] (II) Using input driver 'wacom' for '         WALTOP             Tablet    '
[    27.730] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    27.730] (**)          WALTOP             Tablet    : always reports core events
[    27.730] (**) Option "Device" "/dev/input/event7"
[    27.732] (II)          WALTOP             Tablet    : type not specified, assuming 'stylus'.
[    27.732] (II)          WALTOP             Tablet    : other types will be automatically added.
[    27.732] (--)          WALTOP             Tablet     stylus: using pressure threshold of 27 for button 1
[    27.732] (--)          WALTOP             Tablet     stylus: Wacom USB Graphire4 tablet maxX=12288 maxY=9216 maxZ=1023 resX=80000 resY=80000  tilt=disabled
[    27.732] (II)          WALTOP             Tablet     stylus: hotplugging dependent devices.
[    27.732] (**)          WALTOP             Tablet     eraser: Applying InputClass "evdev pointer catchall"
[    27.732] (**)          WALTOP             Tablet     eraser: Applying InputClass "evdev tablet catchall"
[    27.732] (**)          WALTOP             Tablet     eraser: Applying InputClass "Waltop on wacom class"
[    27.732] (II) Using input driver 'wacom' for '         WALTOP             Tablet     eraser'
[    27.732] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    27.732] (**)          WALTOP             Tablet     eraser: always reports core events
[    27.732] (**) Option "Device" "/dev/input/event7"
[    27.732] (--)          WALTOP             Tablet     eraser: Wacom USB Graphire4 tablet maxX=12288 maxY=9216 maxZ=1023 resX=80000 resY=80000  tilt=disabled
[    27.736] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input7/event7"
[    27.736] (II) XINPUT: Adding extended input device "         WALTOP             Tablet     eraser" (type: ERASER)
[    27.736] (--)          WALTOP             Tablet     eraser: top X=0 top Y=0 bottom X=12288 bottom Y=9216 resol X=80000 resol Y=80000
[    27.736] (**)          WALTOP             Tablet     eraser: (accel) keeping acceleration scheme 1
[    27.736] (**)          WALTOP             Tablet     eraser: (accel) acceleration profile 0
[    27.736] (**)          WALTOP             Tablet     eraser: (accel) acceleration factor: 2.000
[    27.736] (**)          WALTOP             Tablet     eraser: (accel) acceleration threshold: 4
[    27.740] (**)          WALTOP             Tablet     pad: Applying InputClass "evdev pointer catchall"
[    27.740] (**)          WALTOP             Tablet     pad: Applying InputClass "evdev tablet catchall"
[    27.740] (**)          WALTOP             Tablet     pad: Applying InputClass "Waltop on wacom class"
[    27.740] (II) Using input driver 'wacom' for '         WALTOP             Tablet     pad'
[    27.740] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    27.740] (**)          WALTOP             Tablet     pad: always reports core events
[    27.740] (**) Option "Device" "/dev/input/event7"
[    27.744] (--)          WALTOP             Tablet     pad: Wacom USB Graphire4 tablet maxX=12288 maxY=9216 maxZ=1023 resX=80000 resY=80000  tilt=disabled
[    27.744] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input7/event7"
[    27.744] (II) XINPUT: Adding extended input device "         WALTOP             Tablet     pad" (type: PAD)
[    27.744] (**)          WALTOP             Tablet     pad: (accel) keeping acceleration scheme 1
[    27.744] (**)          WALTOP             Tablet     pad: (accel) acceleration profile 0
[    27.744] (**)          WALTOP             Tablet     pad: (accel) acceleration factor: 2.000
[    27.744] (**)          WALTOP             Tablet     pad: (accel) acceleration threshold: 4
[    27.744] (II)          WALTOP             Tablet     stylus: hotplugging completed.
[    27.748] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input7/event7"
[    27.748] (II) XINPUT: Adding extended input device "         WALTOP             Tablet     stylus" (type: STYLUS)
[    27.748] (--)          WALTOP             Tablet     stylus: top X=0 top Y=0 bottom X=12288 bottom Y=9216 resol X=80000 resol Y=80000
[    27.748] (**)          WALTOP             Tablet     stylus: (accel) keeping acceleration scheme 1
[    27.748] (**)          WALTOP             Tablet     stylus: (accel) acceleration profile 0
[    27.748] (**)          WALTOP             Tablet     stylus: (accel) acceleration factor: 2.000
[    27.748] (**)          WALTOP             Tablet     stylus: (accel) acceleration threshold: 4
[    27.749] (II) config/udev: Adding input device          WALTOP             Tablet     (/dev/input/mouse1)
[    27.749] (II) No input driver/identifier specified (ignoring)
```
So it looks like the tablet is matched to the Wacom X driver and everything is good.  But a little later on this happens:
```
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.376] (EE)          WALTOP             Tablet     stylus: Error reading wacom device : No such device
[  7228.377] (II) config/udev: removing device          WALTOP             Tablet     eraser
[  7228.377] (II) UnloadModule: "wacom"
[  7228.378] (II) Unloading wacom
[  7228.378] (II) config/udev: removing device          WALTOP             Tablet     pad
[  7228.378] (II) UnloadModule: "wacom"
[  7228.378] (II) Unloading wacom
[  7228.378] (II) config/udev: removing device          WALTOP             Tablet     stylus
[  7228.404] (II)          WALTOP             Tablet     stylus: removing automatically added devices.
[  7228.404] (II) UnloadModule: "wacom"
[  7228.404] (II) Unloading wacom
```
Maybe the connection between the tablet and your computer is being interrupted?  Make sure the usb cable is firmly seated on both ends.  If you have it plugged into a hub try plugging it in directly at least for now.

Another thought is the stylus battery may be weak.  When was it last replaced?  Does the tablet work plugged into another computer or OS?

---

