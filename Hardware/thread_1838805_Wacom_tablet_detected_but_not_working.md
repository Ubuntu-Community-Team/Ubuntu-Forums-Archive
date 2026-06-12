---
title: "Wacom tablet detected but not working"
date: 2011-09-04
forum: Hardware
---

### Post by vivekkhurana on 2011-09-04
I am trying to get Wacom Bamboo1 Medium tablet (productid=0x6b) working on ubuntu. The tablet is detected with latest input-wacom drivers but the dsktop cursor doesnt move when the pen is moved. The relevant output from X.org log is here 

```


[    99.450] (II) config/udev: Adding input device Wacom Bamboo1 5x8 (/dev/input/mouse1)
[    99.450] (II) No input driver/identifier specified (ignoring)
[    99.451] (II) config/udev: Adding input device Wacom Bamboo1 5x8 (/dev/input/event5)
[    99.451] (**) Wacom Bamboo1 5x8: Applying InputClass "evdev tablet catchall"
[    99.451] (**) Wacom Bamboo1 5x8: Applying InputClass "Wacom class"
[    99.451] (II) LoadModule: "wacom"
[    99.451] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    99.458] (II) Module wacom: vendor="X.Org Foundation"
[    99.458]     compiled for 1.9.99.902, module version = 0.10.11
[    99.458]     Module class: X.Org XInput Driver
[    99.458]     ABI class: X.Org XInput driver, version 12.3
[    99.458] (II) Using input driver 'wacom' for 'Wacom Bamboo1 5x8'
[    99.458] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    99.458] (**) Wacom Bamboo1 5x8: always reports core events
[    99.458] (**) Option "Device" "/dev/input/event5"
[    99.472] (II) Wacom Bamboo1 5x8: type not specified, assuming 'stylus'.
[    99.472] (II) Wacom Bamboo1 5x8: other types will be automatically added.
[    99.472] (--) Wacom Bamboo1 5x8 stylus: using pressure threshold of 27 for button 1
[    99.472] (--) Wacom Bamboo1 5x8 stylus: Wacom Unknown USB tablet maxX=21648 maxY=13530 maxZ=1023 resX=1016 resY=1016  tilt=enabled
[    99.472] (II) Wacom Bamboo1 5x8 stylus: hotplugging dependent devices.
[    99.472] (**) Wacom Bamboo1 5x8 eraser: Applying InputClass "evdev tablet catchall"
[    99.472] (**) Wacom Bamboo1 5x8 eraser: Applying InputClass "Wacom class"
[    99.472] (**) Wacom Bamboo1 5x8 eraser: Applying InputClass "Wacom Bamboo eraser options"
[    99.472] (II) Using input driver 'wacom' for 'Wacom Bamboo1 5x8 eraser'
[    99.472] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    99.472] (**) Wacom Bamboo1 5x8 eraser: always reports core events
[    99.472] (**) Option "Device" "/dev/input/event5"
[    99.488] (**) Option "PressCurve" "5,0,100,95"
[    99.488] (--) Wacom Bamboo1 5x8 eraser: Wacom Unknown USB tablet maxX=21648 maxY=13530 maxZ=1023 resX=1016 resY=1016  tilt=enabled
[    99.488] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input5/event5"
[    99.488] (II) XINPUT: Adding extended input device "Wacom Bamboo1 5x8 eraser" (type: ERASER)
[    99.488] (--) Wacom Bamboo1 5x8 eraser: top X=0 top Y=0 bottom X=21648 bottom Y=13530 resol X=1016 resol Y=1016
[    99.488] (**) Wacom Bamboo1 5x8 eraser: (accel) keeping acceleration scheme 1
[    99.488] (**) Wacom Bamboo1 5x8 eraser: (accel) acceleration profile 0
[    99.488] (**) Wacom Bamboo1 5x8 eraser: (accel) acceleration factor: 2.000
[    99.488] (**) Wacom Bamboo1 5x8 eraser: (accel) acceleration threshold: 4
[    99.488] (**) Wacom Bamboo1 5x8 cursor: Applying InputClass "evdev tablet catchall"
[    99.488] (**) Wacom Bamboo1 5x8 cursor: Applying InputClass "Wacom class"
[    99.488] (**) Wacom Bamboo1 5x8 cursor: Applying InputClass "Wacom Bamboo cursor options"
[    99.489] (II) Using input driver 'wacom' for 'Wacom Bamboo1 5x8 cursor'
[    99.489] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    99.489] (**) Wacom Bamboo1 5x8 cursor: always reports core events
[    99.489] (**) Option "Device" "/dev/input/event5"
[    99.489] (**) Option "Button1" "1"
[    99.489] (**) Option "Button2" "2"
[    99.489] (**) Option "Button3" "3"
[    99.489] (--) Wacom Bamboo1 5x8 cursor: Wacom Unknown USB tablet maxX=21648 maxY=13530 maxZ=1023 resX=1016 resY=1016  tilt=enabled
[    99.489] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input5/event5"
[    99.489] (II) XINPUT: Adding extended input device "Wacom Bamboo1 5x8 cursor" (type: CURSOR)
[    99.489] (--) Wacom Bamboo1 5x8 cursor: top X=0 top Y=0 bottom X=21648 bottom Y=13530 resol X=1016 resol Y=1016
[    99.489] (**) Wacom Bamboo1 5x8 cursor: (accel) keeping acceleration scheme 1
[    99.489] (**) Wacom Bamboo1 5x8 cursor: (accel) acceleration profile 0
[    99.489] (**) Wacom Bamboo1 5x8 cursor: (accel) acceleration factor: 2.000
[    99.489] (**) Wacom Bamboo1 5x8 cursor: (accel) acceleration threshold: 4
[    99.489] (II) Wacom Bamboo1 5x8 stylus: hotplugging completed.
[    99.489] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input5/event5"
[    99.489] (II) XINPUT: Adding extended input device "Wacom Bamboo1 5x8 stylus" (type: STYLUS)
[    99.490] (--) Wacom Bamboo1 5x8 stylus: top X=0 top Y=0 bottom X=21648 bottom Y=13530 resol X=1016 resol Y=1016
[    99.490] (**) Wacom Bamboo1 5x8 stylus: (accel) keeping acceleration scheme 1
[    99.490] (**) Wacom Bamboo1 5x8 stylus: (accel) acceleration profile 0
[    99.490] (**) Wacom Bamboo1 5x8 stylus: (accel) acceleration factor: 2.000
[    99.490] (**) Wacom Bamboo1 5x8 stylus: (accel) acceleration threshold: 4

```The output of xsetwacom is following

```

root@copper:~# xsetwacom --list
Wacom Bamboo1 5x8 eraser            id: 10    type: ERASER    
Wacom Bamboo1 5x8 cursor            id: 11    type: CURSOR    
Wacom Bamboo1 5x8 stylus            id: 12    type: STYLUS  

```The output of xinput is following

```

root@copper:~# xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo1 5x8 eraser                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo1 5x8 cursor                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo1 5x8 stylus                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]


``` So you can see that the tablet is detected by the xorg and driver is loaded but the cursor is not moving. Am I missing anything in the config?

---

### Post by Favux on 2011-09-04
Hi vivekkhurana,

Welcome to Ubuntu forums!

From your Xorg.0.log I see you have xf86-input-wacom0.10.11 so I assume you are in Natty.

Right now your model, which is new, isn't in either the default Natty kernel driver wacom.ko or the Wacom X driver xf86-input-wacom.  So you will need to update both.  Please see the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or the [linux wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") for instructions on installing input-wacom and xf86-input-wacom.

---

### Post by vivekkhurana on 2011-09-04
> **Favux said:**
> Hi vivekkhurana,

Welcome to Ubuntu forums!

From your Xorg.0.log I see you have xf86-input-wacom0.10.11 so I assume you are in Natty.

Right now your model, which is new, isn't in either the default Natty kernel driver wacom.ko or the Wacom X driver xf86-input-wacom.  So you will need to update both.  Please see the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or the [linux wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") for instructions on installing input-wacom and xf86-input-wacom.
Built both input-wacom and xf86-input-wacom from source but no luck. The device is detected but not working. I can repost the logs if required.

---

### Post by Favux on 2011-09-04
Sorry, I should have said you need to clone the git repository of xf86-input-wacom (part II. c of the BambooPT HOW TO).  If you used the xf86-input-wacom-0.11.1 tar the 6b didn't make it into that point release.  Hopefully that's the problem.

---

### Post by vivekkhurana on 2011-09-05
Building from git source did the trick.

Thanks :)

---

