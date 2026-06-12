---
title: "Synaptics Touchpad not recognized as such on new HP Spectre 13 x2 laptop"
date: 2013-12-17
forum: Hardware
---

### Post by pgratz on 2013-12-17
I recently purchased an HP Spectre 13 x2 laptop.  This is a fairly new hybrid tablet/laptop model so I knew I was in for a bit of hassle getting things working ([see my trials/tribulations here]("http://cesg.tamu.edu/faculty/paul-gratz/personal/linux-on-the-hp-spectre-13-x2/")).  Anyways, the Touchpad on the laptop is a synaptics touch pad and it has higher order functions that I've used in Windows on this machine, in Kubuntu and Ubuntu, this touchpad just works as a basic, single touch touchpad.  

Here is the output of xinput:
```
pgratz@pgratz-HP-Spectre-13-x2:~$ xinput &#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynapticsTouch Pad V 1.03U2               id=8    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                          id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; HP TrueVision Full HD                     id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                            id=12   [slave  keyboard (3)]

```

Here are the pertinent lines out of dmesg:
```
[    2.548342] usb 1-1.6: new full-speed USB device number 5 using ehci-pci
[    2.642370] usb 1-1.6: New USB device found, idVendor=06cb, idProduct=5711
[    2.642375] usb 1-1.6: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.642379] usb 1-1.6: Product: SynapticsTouch Pad V 1.03U2
[    2.648413] input: SynapticsTouch Pad V 1.03U2 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3
[    2.649754] hid-generic 0003:06CB:5711.0002: input,hiddev0,hidraw0: USB HID v1.11 Mouse [SynapticsTouch Pad V 1.03U2] on usb-0000:00:1d.0-1.6/input0

```

However, when I run kde's "Touchpad configuration" I get "No Touchpad found".  Can anyone give me some clues on debugging this?
Thanks!
Pau

---

### Post by pgratz on 2013-12-18
A polite *bump*

---

### Post by pgratz on 2013-12-19
Another polite *bump*

---

### Post by pgratz on 2013-12-20
Another polite bump...  Just a pointer to where to go next would be a great help.

---

### Post by pgratz on 2013-12-20
I've filed a bug on this [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1255407](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1255407) .  Please mark it as "affects you" if you see a similar problem on your hardware.  I suspect this isn't the only new laptop with this problem....
Paul

---

### Post by pgratz on 2013-12-22
*bump*

---

### Post by Vormeph on 2013-12-22
If a touchpad isn't recognised, then it's safe to assume that the drivers haven't been installed or configured correctly. I suggest scouting for the driver on the repositories, which should really be there. 

```
sudo apt-get install xserver-xorg-input-synaptics
``` might work for you. If that's already installed, then try turning on the touchpad. On my laptop it's Fn+F9 but yours can be different. If your touchpad still doesn't work, then it's possible that your hardware isn't supported. Since it's really just a touchpad, a simple mouse might do the trick!

---

### Post by Andross707 on 2014-01-09
I have the same computer and the same problem *bump*

---

### Post by Andross707 on 2014-01-18
I tried ```
sudo apt-get install xserver-xorg-input-synaptics
``` and nothing changed. It says this is already the newest version.

---

### Post by Andross707 on 2014-01-29
Something that might be of help is the Xorg.0.log output:

```

clifford@clifford-HP-Spectre-13-x2-PC:~$ cat /var/log/Xorg.0.log | grep -i synaptics
[     5.418] (II) config/udev: Adding input device Synaptics Touch Pad V 103u9 (/dev/input/event4)
[     5.418] (**) Synaptics Touch Pad V 103u9: Applying InputClass "evdev pointer catchall"
[     5.418] (II) Using input driver 'evdev' for 'Synaptics Touch Pad V 103u9'
[     5.418] (**) Synaptics Touch Pad V 103u9: always reports core events
[     5.418] (**) evdev: Synaptics Touch Pad V 103u9: Device: "/dev/input/event4"
[     5.418] (--) evdev: Synaptics Touch Pad V 103u9: Vendor 0x6cb Product 0x5711
[     5.418] (--) evdev: Synaptics Touch Pad V 103u9: Found 3 mouse buttons
[     5.418] (--) evdev: Synaptics Touch Pad V 103u9: Found relative axes
[     5.418] (--) evdev: Synaptics Touch Pad V 103u9: Found x and y relative axes
[     5.418] (II) evdev: Synaptics Touch Pad V 103u9: Configuring as mouse
[     5.418] (**) evdev: Synaptics Touch Pad V 103u9: YAxisMapping: buttons 4 and 5
[     5.418] (**) evdev: Synaptics Touch Pad V 103u9: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.418] (II) XINPUT: Adding extended input device "Synaptics Touch Pad V 103u9" (type: MOUSE, id 8)
[     5.418] (II) evdev: Synaptics Touch Pad V 103u9: initialized for relative axes.
[     5.419] (**) Synaptics Touch Pad V 103u9: (accel) keeping acceleration scheme 1
[     5.419] (**) Synaptics Touch Pad V 103u9: (accel) acceleration profile 0
[     5.419] (**) Synaptics Touch Pad V 103u9: (accel) acceleration factor: 2.000
[     5.419] (**) Synaptics Touch Pad V 103u9: (accel) acceleration threshold: 4
[     5.419] (II) config/udev: Adding input device Synaptics Touch Pad V 103u9 (/dev/input/mouse0)

```

It seems to be applying the "input class" evdev. Some other forums pointed me to a configuration directory:

/usr/share/X11/xorg.conf.d/

A line about the "evdev pointer catchall" is located in /usr/share/X11/xorg.conf.d/10-evdev.conf for me. It seems like /usr/share/X11/xorg.conf.d/50-synaptics.conf isn't being read. I tried to comment out the "evdev pointer catchall" line in 10-evdev.conf, but that just disabled the pointer completely (had to use keyboard shortcuts to edit the file again). Does this give anyone any ideas on this topic?

---

### Post by Andross707 on 2014-02-09
*bump*

---

### Post by Andross707 on 2014-02-18
*bump*

as far as functionality, the touchpad acts as if it only has one button (i.e. not even two finger right click)

---

