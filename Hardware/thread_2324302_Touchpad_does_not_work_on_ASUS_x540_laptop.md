---
title: "Touchpad does not work on ASUS x540 laptop"
date: 2016-05-12
forum: Hardware
---

### Post by Zammael on 2016-05-12
Hello, and it's good to be back among serious computer-folk. 
Unfortunately, I return only to offer complaints, after having exhausted other options (google, browser this forum, harass overworked and underpaid techies, etc. 

First, after installing Ubuntu 16.04 on the ASUS x540 laptop for a dual boot with Windows 10, the touchpad was working on the first clean boot. Then I installed several packages to get started, and then switched to Windows. Upon switching back, the touchpad went dead. Enter google results: I tried the "sudo modprobe psmouse" trick to no avail. 

Xinput list results: 
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer 1600dpi Mouse                   id=9    [slave  pointer  (2)]
&#9116;   &#8627; Elan Touchpad                               id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 VGA UVC WebCam                       id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```

The Touchpad is visible, at least. Typing "dmesg | tail" to see what's wrong turned up this: 
```
[ 2054.461819] elan_i2c i2c-ELAN1000:00: invalid report id data (1)
[ 2054.481253] elan_i2c i2c-ELAN1000:00: invalid report id data (1)
[ 2058.583927] usb 1-1: new low-speed USB device number 6 using xhci_hcd
[ 2058.901614] usb 1-1: New USB device found, idVendor=1532, idProduct=0001
[ 2058.901618] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2058.901621] usb 1-1: Product: Razer 1600dpi Mouse
[ 2058.901623] usb 1-1: Manufacturer: Razer
[ 2058.901775] usb 1-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 2058.906988] input: Razer Razer 1600dpi Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:1532:0001.0002/input/input13
[ 2058.907170] hid-generic 0003:1532:0001.0002: input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi Mouse] on usb-0000:00:14.0-1/input0


```

Then I browsed this forum, having solved many of my problems in the past with Ubuntu 10.04 when I was a greenhorned rookie, and found this link:
[http://askubuntu.com/questions/506826/asus-laptop-touchpad-not-working](http://askubuntu.com/questions/506826/asus-laptop-touchpad-not-working)

Nothing doing. Now, the touchpad might be working at some point in the future, but I'd like to know exactly why, and how I can help others avoid this bug. 
Thanks for your time. :)

---

### Post by Zammael on 2016-05-13
Update: The touchpad works on occasion, when I restart the laptop and switch OSes. But I can't figure out how to make the touchpad work permanently, not every second or third reboot. :-/

---

