---
title: "Cut off power in usb ports?"
date: 2008-11-20
forum: General Help
---

### Post by lambdacore on 2008-11-20
Is there any way to cut the power that goes to the usb ports?
Not just disable them or unmount, really no voltage.
And to do it not from the bios, but with a command line?

Because well I just made some christmas lights that are powered by the usb ports on my laptop. I thought that if I could disable/enable the usb port, I could like do a very simple script to make them flash.

Yeah, holiday's spirit got me already.

Oh I have Ubuntu 8.10 and a crappy Acer Aspire 3050.

Thanks ;)

---

### Post by fragos on 2008-11-21
Most systems today leave power to USB ports even when shut down. With my desktop after shutdown I turn off the power strip everything is connected to. With the laptop the only way to totaly disconnect power is to pull the battery. Not what you wanted to hear for shure. You might try looking in the BIOS setup for the option you want.

---

### Post by ibuclaw on 2008-11-21
I think it is one or more of the following modules that controls the USB power:

```

hci_usb
usbhid
uhci_hcd
ehci_hcd
ohci_hcd

```

To remove them... use "**rmmod**" or "**modprobe -r**"

ie:
```
sudo rmmod hci_usb
```

To get a vague idea of which modules are running on your machine, run "**lsmod**"

Regards
Iain

---

