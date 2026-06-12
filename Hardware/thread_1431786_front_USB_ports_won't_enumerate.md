---
title: "front USB ports won't enumerate"
date: 2010-03-17
forum: Hardware
---

### Post by pickarooney on 2010-03-17
For the lst three days I've been having problems with the USB ports on the front of my PC, neither of which will recognise any USB storage device. All the 4 devices I tried will mount fine in the rear ports of my desktop.

I get output like this from dmesg:
```
[  940.784036] usb 2-4: device descriptor read/64, error -62
[  941.064043] usb 2-4: new full speed USB device using ohci_hcd and address 5
[  941.480038] usb 2-4: device not accepting address 5, error -62
[  941.656052] usb 2-4: new full speed USB device using ohci_hcd and address 6
[  942.064032] usb 2-4: device not accepting address 6, error -62
[  942.064055] hub 2-0:1.0: unable to enumerate USB device on port 4
[  984.452046] usb 1-3: new high speed USB device using ehci_hcd and address 6
```

Am I just unlucky in that the ports 'broke' both at once for no apparent reason or can there be some explanation for their sudden failure to enumerate anything?

---

### Post by sikander3786 on 2010-03-17
Hi.

Have your front USB ports worked for you ever before? Sounds like some hardware issue not related to the OS.

Did you open the casing of your PC in the recent past? Might be you accidently removed USB cables off the motherboard.

Either way I'll recommend to check your motherboard manual and front USB port's cables accordingly.

Regards.

Sikander.

---

### Post by pickarooney on 2010-03-17
They worked fine until a couple of days ago and I haven't changed anything hardware-wise since. 
I will boot with a live CD and see if there is also a problem there. 

Thanks

---

### Post by Grenage on 2010-03-17
> Am I just unlucky in that the ports 'broke' both at once for no apparent reason

Both ports will, in all likelihood, be connected by one cable to one connector; it's a serial bus after all. :)

---

### Post by pickarooney on 2010-03-17
They do recognise that a device is attached and the light on my memory stick flashes as though it was recognised, which is strange. I would have thought with a dodgy cable the ports wouldn't do anything at all. Maybe the motherboard though.

---

### Post by pickarooney on 2010-03-28
I finally got around to testing with a Live CD (Mint 8) and the problem is the same, so it's presumably a hardware issue. 

I'll try check the cables but have no idea what to look for really!

---

