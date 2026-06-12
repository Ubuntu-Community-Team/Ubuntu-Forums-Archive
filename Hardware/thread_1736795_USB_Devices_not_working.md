---
title: "USB Devices not working"
date: 2011-04-22
forum: Hardware
---

### Post by Boomn4x4 on 2011-04-22
I have just installed a fresh version of Ubuntu 10.10 on my Gateway laptop.  Everything is going okay, but I'm stumped on my USB ports... They don't seem to be working.

According to DMESG, its detected... but that is about it.
[ 1268.833000] lo: Disabled Privacy Extensions
[257642.344084] usb 1-4: new high speed USB device using ehci_hcd and address 2
[257766.556068] usb 1-3: new high speed USB device using ehci_hcd and address 3
[257772.943535] usb 1-4: USB disconnect, address 2
[257773.212070] usb 1-4: new high speed USB device using ehci_hcd and address 4
[257778.284098] hub 1-0:1.0: unable to enumerate USB device on port 4
[258049.025839] usb 1-3: USB disconnect, address 3
[258050.836081] usb 1-1: new high speed USB device using ehci_hcd and address 5
[258155.868078] usb 1-1: USB disconnect, address 5
[258696.788073] usb 1-4: new high speed USB device using ehci_hcd and address 6
[259270.624065] usb 1-2: new high speed USB device using ehci_hcd and address 7
[259353.919901] usb 1-2: USB disconnect, address 7
[259379.193718] usb 1-4: USB disconnect, address 6
[259387.316074] usb 1-1: new high speed USB device using ehci_hcd and address 8
[259392.643878] usb 1-1: USB disconnect, address 8
[259395.144052] usb 1-3: new high speed USB device using ehci_hcd and address 9
[259401.948369] usb 1-3: USB disconnect, address 9
[259403.056084] usb 1-4: new high speed USB device using ehci_hcd and address 10
[259410.756278] usb 1-4: USB disconnect, address 10
[259415.996066] usb 1-4: new high speed USB device using ehci_hcd and address 11

I was orginally trying to get an iMicro webcam working, but when it didn't, I tried using a USB flash drive.  Neither one of them worked.... though the messages from mget showed me plugging them in and pulling them out.

I plugged the USB drive into another Ubuntu desktop system, and it recognized and worked just fine.

Any help would be appreciated.

As a quick edit... I just installed cheese on the desktop system, plugged the camera in and it works fine, so I know it is something on the laptop

---

### Post by Nasair on 2011-04-22
I probably won't be able to help much at all, but is your keyboard or  mouse working? I'm making an assumption that at least one of those is  USB. Just wondering if anything will work on the new install.

---

### Post by Boomn4x4 on 2011-04-22
Yes, keyboard and touchpad mouse working just fine.

---

### Post by Nasair on 2011-04-22
Can you see the camera as a USB device on the laptop?
Try in the terminal:
```
xinput list
```

Should see something like this:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech BT Mini-Receiver          id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech Logitech BT Mini-Receiver          id=8    [slave  keyboard (3)]
    &#8627; HID 3351:3715                               id=10    [slave  keyboard (3)]

```

---

### Post by Boomn4x4 on 2011-04-22
> **Nasair said:**
> Can you see the camera as a USB device on the laptop?
Try in the terminal:
```
xinput list
```Should see something like this:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech BT Mini-Receiver          id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech Logitech BT Mini-Receiver          id=8    [slave  keyboard (3)]
    &#8627; HID 3351:3715                               id=10    [slave  keyboard (3)]

```


No.... Dosen't see anything other than the mouse or keyboard

```
michael@gateway-laptop:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

```

---

### Post by Nasair on 2011-04-22
Bang, that is the issue then. I'm having a similar issue with my XBox 360 wireless controller, but I can actually getting it working through another program...any ways I'm still waiting on that myself so sorry but I can't help further. In summary, you need to figure out why Ubuntu isn't adding your webcam as a usb device but is adding others.

---

### Post by Boomn4x4 on 2011-04-22
When in doubt.... Reboot.

Problem resolved...

---

### Post by Nasair on 2011-04-22
Lol :d

---

