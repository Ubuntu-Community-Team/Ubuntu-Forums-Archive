---
title: "Samsung Intercept USB"
date: 2010-11-26
forum: Hardware
---

### Post by Emblem Parade on 2010-11-26
Anyone had luck connecting this via USB?

Couldn't on Ubuntu 10.10. Here is what I've discovered:

1. lsusb hangs while the device is connected. As soon as I disconnect the device, lsusb succeeds (and of course doesn't show the device).

2. Tried to disable USB 2.0, but the old method (sudo modprobe -r ohci_hcd) doesn't work in the new kernels anymore.

3. dmesg output:
```

[14774.061307] usb 2-2: new high speed USB device using ehci_hcd and address 4
[14788.381328] hub 2-0:1.0: unable to enumerate USB device on port 2
[14794.500080] usb 2-2: new high speed USB device using ehci_hcd and address 5
[14809.621308] usb 2-2: device descriptor read/64, error -110
[14824.850058] usb 2-2: device descriptor read/64, error -110
[14825.083229] usb 2-2: new high speed USB device using ehci_hcd and address 6
[14840.200056] usb 2-2: device descriptor read/64, error -110
[14855.430109] usb 2-2: device descriptor read/64, error -110
[14855.660068] usb 2-2: new high speed USB device using ehci_hcd and address 7
[14861.080358] usb 2-2: device not accepting address 7, error -71
[14861.200686] usb 2-2: new high speed USB device using ehci_hcd and address 8
[14866.621295] usb 2-2: device not accepting address 8, error -71
[14866.621325] hub 2-0:1.0: unable to enumerate USB device on port 2
[14867.011319] usb 5-2: new full speed USB device using ohci_hcd and address 2
[14882.181304] usb 5-2: device descriptor read/64, error -110
[14897.460062] usb 5-2: device descriptor read/64, error -110
[14897.720063] usb 5-2: new full speed USB device using ohci_hcd and address 3
[14912.870046] usb 5-2: device descriptor read/64, error -110
[14928.131316] usb 5-2: device descriptor read/64, error -110
[14928.411312] usb 5-2: new full speed USB device using ohci_hcd and address 4
[14933.831297] usb 5-2: device not accepting address 4, error -62
[14933.980069] usb 5-2: new full speed USB device using ohci_hcd and address 5
[14939.401300] usb 5-2: device not accepting address 5, error -62

```

4. "USB debugging" mode on the device doesn't seem to have an effect either way.

5. Tried it with a different USB cable, too.

6. Tried it on my other Ubuntu machine (10.10 32 bit). Exactly the same effect, so it's not an AMD64 issue, nor a motherboard/hardware issue.

7. Could not get it working on Windows 7 64 bit, either. The OS sees it as an unrecognized device, at least. (Samsung only has 32 bit drivers available on its site, and I don't have a 32 bit Windows machine.)

In any case, very worried about Ubuntu/Linux's behavior with USB in this case. Shouldn't at least lsusb work?

Any ideas would be appreciated!

---

### Post by Emblem Parade on 2010-12-02
I have a liftoff. :)

In my case, it ended up being a combination of two things.

First, I had to disable the USB 2.0 driver (ehci_hcd). To do this on kernels since Karmic, where echi_hcd is compiled into the kernel, you need to unbind the driver. This worked for me on Maverick.

```

cd /sys/bus/pci/drivers/ehci_hcd
sudo sh -c 'echo -n "0000:00:12.2" > unbind'
sudo sh -c 'echo -n "0000:00:13.2" > unbind'

```

Then, I also found out (so much trial and error!) that one of my USB devices conflicted somehow with the phone. So, I recommend unplugging everything from USB until something works out...

Sigh. I hate computers.

---

### Post by nitrogensixteen on 2011-04-25
I am sure there are many frustrated owners out there who this won't work for. I have a thinkpad T61p which exhibited the same symptoms.
For my system, the fix is to disable the first uhci usb bus.
If unbinding ehci_hcd doesn't work for you, rebind ehci, then unbind and rebind the uhci_hcd busses one by one using the same process as above.

---

