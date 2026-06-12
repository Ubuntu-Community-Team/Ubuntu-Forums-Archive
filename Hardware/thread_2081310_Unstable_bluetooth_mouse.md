---
title: "Unstable bluetooth mouse"
date: 2012-11-06
forum: Hardware
---

### Post by KFoder on 2012-11-06
Hi

Since updating to 12.10 I have had problems using my bluetooth mouse :(

The bluetooth indicator shows one connected device, and the mouse thinks it's connected, but it does not work, it was functioning in 12.04 !

If I disconnect the mouse, using the indicator, several times, it always reconnects at once, and now and then starts working for some time, and then suddenly stops again.

I get same result if I remove the device, and register it again, works for some time, and then not :(

Bluetooth is functioning, as I can browse my phone, and transfer files, without any problems, also when the mouse is non functional.

There are no errors in the logs :

Kernel.log :
```

11/06/12 07:42:29 PM    input    Bluetooth Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:12/input18
11/06/12 07:42:29 PM    elecom 0005    56E:0061.0003: input,hidraw0: BLUETOOTH HID v0.1e Mouse [Bluetooth Mouse] on 40:2C:F4:8A:BA:43

```X,org.log
```

    Information    [  3399.241] (II) config/udev: Adding input device Bluetooth Mouse (/dev/input/mouse1)
    Information    [  3403.733] (II) config/udev: removing device Bluetooth Mouse
    Information    [  3403.741] (II) evdev: Bluetooth Mouse: Close
    Information    [  3405.609] (II) config/udev: Adding input device Bluetooth Mouse (/dev/input/mouse1)
    Information    [  3405.610] (II) config/udev: Adding input device Bluetooth Mouse (/dev/input/event16)
    Information    [  3405.611] (**) Bluetooth Mouse: Applying InputClass "evdev pointer catchall"
    Information    [  3405.611] (II) Using input driver 'evdev' for 'Bluetooth Mouse'
    Information    [  3405.611] (**) Bluetooth Mouse: always reports core events
    Information    [  3405.611] (**) evdev: Bluetooth Mouse: Device: "/dev/input/event16"
    Information    [  3405.611] (--) evdev: Bluetooth Mouse: Vendor 0x56e Product 0x61
    Information    [  3405.611] (--) evdev: Bluetooth Mouse: Found 12 mouse buttons
    Information    [  3405.611] (--) evdev: Bluetooth Mouse: Found scroll wheel(s)
    Information    [  3405.611] (--) evdev: Bluetooth Mouse: Found relative axes
    Information    [  3405.611] (--) evdev: Bluetooth Mouse: Found x and y relative axes
    Information    [  3405.611] (II) evdev: Bluetooth Mouse: Configuring as mouse
    Information    [  3405.611] (II) evdev: Bluetooth Mouse: Adding scrollwheel support
    Information    [  3405.611] (**) evdev: Bluetooth Mouse: YAxisMapping: buttons 4 and 5
    Information    [  3405.611] (**) evdev: Bluetooth Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
    Information    [  3405.611] (II) XINPUT: Adding extended input device "Bluetooth Mouse" (type: MOUSE, id 13)
    Information    [  3405.612] (II) evdev: Bluetooth Mouse: initialized for relative axes.
    Information    [  3405.612] (**) Bluetooth Mouse: (accel) keeping acceleration scheme 1
    Information    [  3405.612] (**) Bluetooth Mouse: (accel) acceleration profile 0
    Information    [  3405.612] (**) Bluetooth Mouse: (accel) acceleration factor: 2.000
    Information    [  3405.612] (**) Bluetooth Mouse: (accel) acceleration threshold: 4

```Any ideas ?

Kim

---

### Post by CAUPegasus on 2012-11-08
I have the same or very similar problem on a Fujitsu AH531 laptop after a (non-clean) upgrade to 12.10 from 12.04LTS.

Under 12.04, BT mouse worked flawlessly, other than me having to cycle mouse power switch after waking system up from suspend (screen turned off).

In 12.10, I note that the battery indicator now shows 2 batteries: one is the laptop, and the other new one is the mouse battery. Clicking on this and opening the power management window causes the mouse to drop off line instantly. When the mouse is working, the bluetooth status app shows it as ON but not paired. 

On waking up the system or rebooting it, it takes a time or two of cycling the mouse power switch to get a link. Once this is established, seems to work as well as it did in 12.04. BUT, it seems to take around 15 seconds to get the link up (i.e., cursor responds to mouse movements) in 12.10 whereas in 12.04, it was fairly instantaneous. Again, just clicking on the "indicator-battery" app will kick the BT mouse off line and require the power cycle(s) and long delay to reestablish.

One other observation: moving the mouse can wake the system from suspend (screen turned off), so I know it is working at that point, but as soon as the system is back up, the bluetooth link is broken.

Based on this behavior, I theorize that there is some unfortunate interaction between the 12.10 (or equally likely the 3.5.x kernel) power management scheme and bluetooth.

I have disabled the Screen and Lock features and installed the Xscreensaver and use its power management settings in order to get my BT mouse to be this well-behaved.

I am hopeful that these clues might be useful to the throng of folks that are far more knowledgeable about the kernel internals and 12.10 power management than I.

---

