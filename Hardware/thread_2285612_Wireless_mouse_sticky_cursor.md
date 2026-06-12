---
title: "Wireless mouse sticky cursor"
date: 2015-07-07
forum: Hardware
---

### Post by shyamsg on 2015-07-07
I just got a USB wireless mouse and keyboard set for my office. I am running ubuntu 14.04 on a sony vaio pro 13 laptop with Intel i5-4200U CPU processor with the haswell mobile chipset. The keyboard works well and has no problems at all. The mouse works but if i do not use it (move it or click a button for more than 5 seconds), the cursor freezes on the screen. It is not as if the mouse is not working, but the cursor does not move and only updates the position on the screen when I click a button on the mouse - then it moves to the new position where it has been moved to. The usb keyboard and mouse set is from tecknet in the UK - the model of the set is X600. The output of my xinput is 
```

$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Keyboard Mouse            id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; MOSART Semi. 2.4G Keyboard Mouse            id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```

In addition, these are the only lines in dmesg that are usb related. It looks like the device is functioning ok.
```

$ dmesg | grep usb | tail -20
[    1.685484] usb 2-2: Manufacturer: MOSART Semi.
[    1.685610] usb 2-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.695068] usbcore: registered new interface driver usbhid
[    1.695071] usbhid: USB HID core driver
[    1.697325] input: MOSART Semi. 2.4G Keyboard Mouse as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/input/input6
[    1.697405] hid-generic 0003:062A:4101.0001: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. 2.4G Keyboard Mouse] on usb-0000:00:14.0-2/input0
[    1.697581] input: MOSART Semi. 2.4G Keyboard Mouse as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.1/input/input7
[    1.697703] hid-generic 0003:062A:4101.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G Keyboard Mouse] on usb-0000:00:14.0-2/input1
[    1.755486] usb 1-1.6: new full-speed USB device number 3 using ehci-pci
[    1.850036] usb 1-1.6: New USB device found, idVendor=8087, idProduct=07dc
[    1.850041] usb 1-1.6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.935424] usb 2-1.2: new high-speed USB device number 4 using xhci_hcd
[    1.965650] usb 2-1.2: New USB device found, idVendor=0b95, idProduct=7720
[    1.965655] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.965657] usb 2-1.2: Product: AX88x72A
[    1.965659] usb 2-1.2: Manufacturer: ASIX Elec. Corp.
[    1.965661] usb 2-1.2: SerialNumber: 0003FD
[   21.229267] usbcore: registered new interface driver btusb
[   21.609100] asix 2-1.2:1.0 eth0: register 'asix' at usb-0000:00:14.0-1.2, ASIX AX88772 USB 2.0 Ethernet, 00:0e:c6:fa:ef:a9
[   21.609128] usbcore: registered new interface driver asix

```

Any help on this issue is much appreciated. 
Thanks in advance. 
Shyam

---

### Post by Mike_Walsh on 2015-07-07
Nothing wrong there, that I can see. All looks fine.

You know, mice are funny things. With wireless ones, you tend to get what you pay for.....and you're usually better to stick to well-known brands.

I had a couple of 'cheap'n'cheerful' ones some years ago; battery life was awful, half the time the cursor wouldn't respond (and don't get me started on the scroll-wheels!).......etc., etc. Ever since then, I've stuck to good quality, brand-names. I'm not a 'gamer', but I've never grudged the £50 ($80?) I paid for my Logitech 'ZoneTouch' T400 some 3 or 4 years ago. It simply.....**works**.


Regards,

Mike.

---

### Post by shyamsg on 2015-07-07
Thanks for the reply Mike. I was not sure what was wrong either. Everything looked right. My guess is that the receiver is losing packets. Anyway, I might plug it into another computer to see if it causes similar issues in non-ubuntu distros. If yes, it might be time to look for a better product.

Cheers,
Shyam

---

