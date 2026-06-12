---
title: "apple magic trackpad no movement"
date: 2015-05-03
forum: Hardware
---

### Post by armandke2 on 2015-05-03
Hello everybody,

this is my first post but I try to be as good it should!
I have an apple magic trackpad and try to make it work. bluetooth pairing is ok, but I think I have a problem  loading the driver.  followed several sites but still no result.
**hwinfo gives:**

82: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.249]
  Unique ID: AH6Q.Rs_KqQ+gJf1
  Hardware Class: mouse
  Model: "Apple Wireless Trackpad"
  Vendor: 0x05ac 
  Device: 0x030e "Apple Wireless Trackpad"
  Compatible to: int 0x0210 0x0001
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event19
  Device Number: char 13:63 (char 13:33)
  Driver Info #0:
    Buttons: 1
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

**and the log file of xorg gives:**
[  2128.180] (II) config/udev: Adding input device Apple Wireless Trackpad (/dev/input/mouse1)
[  2128.180] (**) Apple Wireless Trackpad: Ignoring device from InputClass "touchpad ignore duplicates"
[  2128.206] (II) config/udev: Adding input device Apple Wireless Trackpad (/dev/input/event19)
[  2128.206] (**) Apple Wireless Trackpad: Applying InputClass "evdev touchpad catchall"
[  2128.206] (**) Apple Wireless Trackpad: Applying InputClass "evdev touchpad catchall"
[  2128.206] (**) Apple Wireless Trackpad: Applying InputClass "touchpad catchall"
[  2128.206] (**) Apple Wireless Trackpad: Applying InputClass "Default clickpad buttons"
[  2128.206] (**) Apple Wireless Trackpad: Applying InputClass "Disable clickpad buttons on Apple touchpads"
[  2128.206] (**) Apple Wireless Trackpad: Applying InputClass "Apple Magic Trackpad"
[  2128.206] (**) Apple Wireless Trackpad: Applying InputClass "libinput touchpad catchall"
[  2128.206] (II) Using input driver 'libinput' for 'Apple Wireless Trackpad'
[  2128.206] (**) Apple Wireless Trackpad: always reports core events
[  2128.206] (**) Option "Device" "/dev/input/event19"
[  2128.207] (II) input device 'Apple Wireless Trackpad', /dev/input/event19 is tagged by udev as: Touchpad
[  2128.207] (II) input device 'Apple Wireless Trackpad', /dev/input/event19 is a touchpad
[  2128.235] (**) Option "Tapping" "On"
[  2128.235] (**) Option "config_info"  "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/bluetooth/hci0/hci0:6/0005:05AC:030E.0009/input/input23/event19"
[  2128.235] (**) Option "AccelerationScheme" "none"
[  2128.235] (**) Apple Wireless Trackpad: (accel) selected scheme none/0
[  2128.235] (**) Apple Wireless Trackpad: (accel) acceleration factor: 2.000
[  2128.235] (**) Apple Wireless Trackpad: (accel) acceleration threshold: 4
[  2128.235] (II) input device 'Apple Wireless Trackpad', /dev/input/event19 is tagged by udev as: Touchpad
[  2128.235] (II) input device 'Apple Wireless Trackpad', /dev/input/event19 is a touchpad
[  2173.291] (II) config/udev: removing device Apple Wireless Trackpad
[  2173.303] (II) UnloadModule: "libinput"


**I really do not know how to get it work**. with the edev driver  only the hard click worked. changing to synaptics driver with no result.  I made and extra file in xorg.conf.d as descriped on many sites  (60-apple-magic-trackpad.conf).  gsynaptics loads but settings do not  change a thing. 
the kde touchmodule most often say that the saved settings are different  from the actual settings? sometimes a message that no touchpad is found  and sometimes crashing (kde5).

anybody could point me in the right direction?

after one year really would want to see that grey thing doing at least a movement with the arrow!
thank you in advance!

---

### Post by lana-jan on 2015-10-21
I have problem with my magic trackpad with similar behaviour - my assumption is that the magic device could communicate in different protocols, but the linux driver expects just one - see my question at [stackexchange: magic trackpad protocol modes]("http://apple.stackexchange.com/questions/210631/magic-trackpad-protocol-modes")

---

