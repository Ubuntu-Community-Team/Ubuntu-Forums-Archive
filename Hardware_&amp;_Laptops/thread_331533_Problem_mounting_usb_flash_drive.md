---
title: "Problem mounting usb flash drive"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by zgerrz on 2007-01-04
I'm trying to mount this usb flash drive that houses a 1GB SD card. It doesn't automount when plugged in, and it doesn't show up in the output after lsusb command is issued. It also doesn't show up when sudo fdisk -l is run. Here is the output of dmesg

```
[17199092.756000] usb 5-6: new high speed USB device using ehci_hcd and address 19
[17199093.164000] usb 5-6: device not accepting address 19, error -71
[17199093.276000] usb 5-6: new high speed USB device using ehci_hcd and address 20
[17199093.684000] usb 5-6: device not accepting address 20, error -71
[17199239.608000] usb 5-6: new high speed USB device using ehci_hcd and address 21
[17199239.720000] usb 5-6: device descriptor read/64, error -71
[17199239.936000] usb 5-6: device descriptor read/64, error -71
[17199240.152000] usb 5-6: new high speed USB device using ehci_hcd and address 22
[17199240.264000] usb 5-6: device descriptor read/64, error -71
[17199240.480000] usb 5-6: device descriptor read/64, error -71
[17199240.696000] usb 5-6: new high speed USB device using ehci_hcd and address 23
[17199241.104000] usb 5-6: device not accepting address 23, error -71
[17199241.216000] usb 5-6: new high speed USB device using ehci_hcd and address 24
[17199241.624000] usb 5-6: device not accepting address 24, error -71
[17199535.216000] usb 5-6: new high speed USB device using ehci_hcd and address 25
[17199535.332000] usb 5-6: device descriptor read/64, error -71
[17199535.552000] usb 5-6: device descriptor read/64, error -71
[17199535.768000] usb 5-6: new high speed USB device using ehci_hcd and address 26
[17199535.884000] usb 5-6: device descriptor read/64, error -71
[17199536.104000] usb 5-6: device descriptor read/64, error -71
[17199536.320000] usb 5-6: new high speed USB device using ehci_hcd and address 27
[17199536.728000] usb 5-6: device not accepting address 27, error -71
[17199536.840000] usb 5-6: new high speed USB device using ehci_hcd and address 28
[17199537.248000] usb 5-6: device not accepting address 28, error -71
```

These results are after repeatedly inserting and removing the drive.

How can I fix this?

---

### Post by zgerrz on 2007-01-04
please help

---

### Post by zgerrz on 2007-01-04
Problem half-way solved for me.

I have 2 usb ports located on the front of my desktop and several more in the back. The front 2 ports resulted in the same unrecognized device, but a usb port on the back appears to work fine.

It's good that I got it to work, but I have to scramble to the back of my tower to insert and remove the drive now! The tower is also tucked away, so this is quite an annoying problem.

Is there someway to remedy this problem?

---

### Post by Spin Doctor on 2008-01-24
Hi there,

I have the exact same problem...exactly same errormessage! I suspect me using my memorystick on a windozesystem...might have done this =P  before I never used with my other PC but recently have....maybe part problem..who knows..

Maybe an expert out there?

---

### Post by Spin Doctor on 2008-01-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 Allright. I have found the following bugreport for this issue. See above. A quick fix seems to run ```
sudo modprobe -r ehci_hcd
```I have verified this and it does work...however it seems you have to run it everytime...and you lose usb2.0 functionality.

The interesting thing with my usbsticks is that I get an error message on Windows saying it is connected as an 1.1 device..so I believe in my case..it is the USB-stick that has failed really...and therefore Ubuntu will not mount it voluntary. 

Hope this helps!

---

