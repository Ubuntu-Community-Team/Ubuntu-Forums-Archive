---
title: "Infrared"
date: 2009-03-30
forum: Hardware
---

### Post by skotos on 2009-03-30
Current status:

[LIST=1]
[*]A **Conceptronic multimedia hard disk remote control** makes my switched off notebook to switch on and boot up (this should be a BIOS related matter though the IRDASIR-A is currently configured as OS manageable).
[*]Every other TV remote control has no effect, but this one is able - when a user is logged on - to always force a count down popup to rise (see attachment).
[/LIST]
 
Since lirc is not installed on my system, which daemon is or might be currently managing the infrared device?

---

### Post by skotos on 2009-03-30
I have just run```
sudo lsmod | grep -i lir
```and I have got the following```
lirc_atiusb            24352  0 
lirc_dev               20020  1 lirc_atiusb
usbcore               149360  8 lirc_atiusb,uvcvideo,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
```I do not think *lirc_atiusb* is the right module (it is simply the one I have specified to *lirc* when I was checking a possible confguration and I thought it had been removed when I had chosen to  "Completely remove the package and its settings" in Synaptic.

---

