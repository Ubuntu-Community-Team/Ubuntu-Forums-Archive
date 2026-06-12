---
title: "FTDI virtual serial port"
date: 2009-08-05
forum: Hardware
---

### Post by estratos on 2009-08-05
Hi,

I have an USB board containing a FTDI FT2232D IC. I have libftdi0 installed in my Ubuntu 8.04 PC and expected it to recognize the USB board as a virtual serial port. However, no ttyUSB* device is created when I plug the board to my PC. I get just the following dmesg lines:

```

467.169089] usb 2-1: new full speed USB device using uhci_hcd and address 5
467.378023] usb 2-1: configuration #1 chosen from 1 choice

```

I've removed brltty and restarted my computer but the problem persists. I must also say that this board can communicate with openocd via the native drivers (no virtual serial port). Of course, I'm trying to try the virtual serial port route when openocd is not running.

Any idea?

Thanks a lot,

Daniel.

---

### Post by halestorm on 2009-11-20
> **estratos said:**
> Hi,

I have an USB board containing a FTDI FT2232D IC. I have libftdi0 installed in my Ubuntu 8.04 PC and expected it to recognize the USB board as a virtual serial port. However, no ttyUSB* device is created when I plug the board to my PC. I get just the following dmesg lines:

```

467.169089] usb 2-1: new full speed USB device using uhci_hcd and address 5
467.378023] usb 2-1: configuration #1 chosen from 1 choice

```

I've removed brltty and restarted my computer but the problem persists. I must also say that this board can communicate with openocd via the native drivers (no virtual serial port). Of course, I'm trying to try the virtual serial port route when openocd is not running.


Did you figure this out? I have the EXACT same problem (except the message displayed contains ... ohci_hcd ... instead of uhci)

---

