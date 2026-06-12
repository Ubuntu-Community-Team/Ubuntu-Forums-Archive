---
title: "Encrypted USB drive not recognised on some machines"
date: 2015-09-15
forum: Hardware
---

### Post by marek_online on 2015-09-15
I have a portable usb drive, encrypted with LUKS, that is immediately recognised and works on my laptop, but won't show up on either of two desktops I use.

All machines are running 14.04. On the desktop machines, dmesg provides errors such as the following:

```
[  322.944033] usb 6-2: new full-speed USB device number 2 using uhci_hcd
[  323.064042] usb 6-2: device descriptor read/64, error -71
[  323.288025] usb 6-2: device descriptor read/64, error -71
[  323.504029] usb 6-2: new full-speed USB device number 3 using uhci_hcd
[  323.624027] usb 6-2: device descriptor read/64, error -71
[  323.848024] usb 6-2: device descriptor read/64, error -71
[  324.064044] usb 6-2: new full-speed USB device number 4 using uhci_hcd
[  324.472029] usb 6-2: device not accepting address 4, error -71
[  324.584041] usb 6-2: new full-speed USB device number 5 using uhci_hcd
[  324.996039] usb 6-2: device not accepting address 5, error -71
[  324.996064] hub 6-0:1.0: unable to enumerate USB device on port 2
```

Searching around suggests either that there's a hardware fault, or I just need to restart the desktops after a few minutes powered off and unplugged.

Powering off and unplugging hasn't worked, and the fact that the device is immediately recognised and mounted without problems on the laptop suggested (to my naive eyes at least) that I don't have a hardware failure on my hands. 

I've also tried connecting the drive using an externally powered USB hub, just in case it was a power to the ports issue. 

I've tried running e2fsck on the drive when it is connected to the laptop. That ran fine but didn't change the problem.

No dice.

The drive contains all of my emails, so I'm keen to figure this one out, and any advice is gratefully received.

Cheers.

---

### Post by marek_online on 2015-09-20
Just bumping this one. No change in anything - still works on the laptop, still the same errors on both desktops.

---

