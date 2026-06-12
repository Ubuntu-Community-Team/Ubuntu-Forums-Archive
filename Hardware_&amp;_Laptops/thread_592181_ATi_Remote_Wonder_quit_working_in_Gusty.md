---
title: "ATi Remote Wonder quit working in Gusty"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by cracker on 2007-10-26
My ATi Remote Wonder, a USB RF remote control, works flawlessly with no configuration on Edgy. I haven't tried it on Feisty, but on Gusty, I get no input from my remote. The kernel module, "ati_remote", is loaded, but I just can't get any input from it. Any ideas?

---

### Post by cracker on 2007-10-27
Nothing? Here's a little extra information if it helps.

Relevant dmesg:
```
[81607.292000] usb 1-6: new low speed USB device using ohci_hcd and address 4
[81607.516000] usb 1-6: string descriptor 0 read error: -22
[81607.532000] usb 1-6: configuration #1 chosen from 1 choice
[81607.596000] lirc_dev: IR Remote Control driver registered, at major 61 
[81607.596000] 
[81607.596000] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[81607.596000] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[81607.600000] lirc_dev: lirc_register_plugin: sample_rate: 0
[81607.608000] lirc_atiusb[4]: X10 Wireless Technology Inc USB Receiver on usb1:4
[81607.624000] usbcore: registered new interface driver lirc_atiusb
[81607.648000] usbcore: registered new interface driver ati_remote
[81607.648000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/misc/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1

```

lsusb:
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver   #This is the remote
Bus 001 Device 003: ID 046d:c041 Logitech, Inc.                               #This is my mouse
Bus 001 Device 001: ID 0000:0000  

```

I can get any other info you need.

---

### Post by greg963 on 2007-10-28
Gutsy has added the lirc drivers for the ati remote to the kernel.  Thus the lirc_atiusb module confilicts with the ati_remote module.  You will have to disable the one you are not using with:

rmmod lirc_atiusb

I think that can be acomplished permanently by adding:

blacklist lirc_atiusb
to /etc/modprobe.d/blacklist

---

### Post by markp1989 on 2008-03-05
> **greg963 said:**
> Gutsy has added the lirc drivers for the ati remote to the kernel.  Thus the lirc_atiusb module confilicts with the ati_remote module.  You will have to disable the one you are not using with:

rmmod lirc_atiusb

I think that can be acomplished permanently by adding:

blacklist lirc_atiusb
to /etc/modprobe.d/blacklist

thankyou so much, worked perfectly

---

