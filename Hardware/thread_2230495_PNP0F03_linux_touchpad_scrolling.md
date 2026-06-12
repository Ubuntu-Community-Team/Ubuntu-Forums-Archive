---
title: "PNP0F03 linux touchpad scrolling"
date: 2014-06-19
forum: Hardware
---

### Post by neanderslob on 2014-06-19
I have a laptop (a cheap OEM generic) that comes equipped with a PNP0F03 touchpad.  This touchpad works very well (tap click, scroll etc) under Windows and works pretty well under Ubuntu.  

The only issue I have with it is that it refuses to scroll up.  When I swipe upward, it moves the page down at 2X speed.  (Not the case under Windows).  To combat this, I've tried installing [this driver ]("http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/"), which I found on a forum post had helped someone with Arch.  The installation went smoothly but did not correct the issue.  I figure there must be an easier way to deal with this, since it reliably recognizes scrolling gestures but just doesn't execute one of them properly.  

Any thoughts would be greatly appreciated.

**For reference:**

```

    kubuntu@kubuntu:~$ xinput list
	&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
	&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
	&#9116;   &#8627; ImExPS/2 Generic Explorer Mouse         	id=12	[slave  pointer  (2)]
	&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
	    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
	    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
	    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
	    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
	    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
	    &#8627; USB2.0 Camera                           	id=10	[slave  keyboard (3)]
	    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```
and
```

	kubuntu@kubuntu:~$ dmesg | grep -i input
	[   10.373029] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
	[   10.376019] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
	[   10.376121] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
	[   10.376215] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
	[   10.464402] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
	[   10.745066] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
	[   41.808030] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input8
	[   42.770426]    inputs:
	[   42.822940] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
	[   42.823275] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
	[   42.823565] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
	[   42.934573] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input7

```
and
```

	kubuntu@kubuntu:~$ cat /sys/class/input/mouse0/device/uevent 
	PRODUCT=11/2/6/0
	NAME="ImExPS/2 Generic Explorer Mouse"
	PHYS="isa0060/serio1/input0"
	PROP=0
	EV=7
	KEY=1f0000 0 0 0 0
	REL=143
	MODALIAS=input:b0011v0002p0006e0000-e0,1,2,k110,111,112,113,114,r0,1,6,8,amlsfw

and

	kubuntu@kubuntu:~$ cat /var/log/Xorg.0.log | grep -i input
	[   122.075] (II) The server relies on udev to provide the list of input devices.
	[   122.075]    X.Org XInput driver : 20.0
	[   122.158] Initializing built-in extension XInputExtension
	[   122.336] (II) modesetting(0): Digital Display Input
	[   122.621] (II) config/udev: Adding input device Power Button (/dev/input/event3)
	[   122.621] (**) Power Button: Applying InputClass "evdev keyboard catchall"
	[   122.622] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
	[   122.623]    Module class: X.Org XInput Driver
	[   122.623]    ABI class: X.Org XInput driver, version 20.0
	[   122.623] (II) Using input driver 'evdev' for 'Power Button'
	[   122.623] (**) evdev: Power Button: Device: "/dev/input/event3"
	[   122.623] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
	[   122.623] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
	[   122.625] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
	[   122.625] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
	[   122.625] (II) Using input driver 'evdev' for 'Video Bus'
	[   122.625] (**) evdev: Video Bus: Device: "/dev/input/event5"
	[   122.625] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event5"
	[   122.625] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
	[   122.627] (II) config/udev: Adding input device Power Button (/dev/input/event2)
	[   122.627] (**) Power Button: Applying InputClass "evdev keyboard catchall"
	[   122.627] (II) Using input driver 'evdev' for 'Power Button'
	[   122.627] (**) evdev: Power Button: Device: "/dev/input/event2"
	[   122.627] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
	[   122.627] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
	[   122.629] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
	[   122.629] (II) No input driver specified, ignoring this device.
	[   122.630] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
	[   122.630] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
	[   122.630] (II) Using input driver 'evdev' for 'Sleep Button'
	[   122.630] (**) evdev: Sleep Button: Device: "/dev/input/event1"
	[   122.630] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
	[   122.630] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
	[   122.632] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
	[   122.632] (II) No input driver specified, ignoring this device.
	[   122.633] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event7)
	[   122.633] (II) No input driver specified, ignoring this device.
	[   122.634] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
	[   122.634] (II) No input driver specified, ignoring this device.
	[   122.635] (II) config/udev: Adding input device USB2.0 Camera (/dev/input/event6)
	[   122.635] (**) USB2.0 Camera: Applying InputClass "evdev keyboard catchall"
	[   122.635] (II) Using input driver 'evdev' for 'USB2.0 Camera'
	[   122.635] (**) evdev: USB2.0 Camera: Device: "/dev/input/event6"
	[   122.635] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input8/event6"
	[   122.635] (II) XINPUT: Adding extended input device "USB2.0 Camera" (type: KEYBOARD, id 10)
	[   122.637] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
	[   122.637] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
	[   122.637] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
	[   122.637] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
	[   122.637] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
	[   122.637] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
	[   122.639] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event10)
	[   122.639] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
	[   122.639] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
	[   122.639] (**) evdev: ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event10"
	[   122.639] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event10"
	[   122.639] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE, id 12)
	[   122.641] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
	[   122.641] (II) No input driver specified, ignoring this device.

```

---

