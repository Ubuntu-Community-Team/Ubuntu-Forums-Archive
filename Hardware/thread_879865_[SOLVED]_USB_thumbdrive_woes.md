---
title: "[SOLVED] USB thumbdrive woes"
date: 2008-08-04
forum: Hardware
---

### Post by lucis on 2008-08-04
I recently installed Ubuntu for a friend and thus far, it has been a great experience for him except for one major problem: neither of his USB thumbdrives seem to work. 

System stats:

Ubuntu Hardy x86 32 bit w/ all updates installed
Custom built machine with off-brand mobo and four USB ports (2 in the back, 2 in the front)
Two thumbdrives: one Lexar brand and one unknown brand

The two USB ports in the back are currently being used by the mouse and keyboard, leaving the two at the front. These ports work fine with any other sort of device (i.e., webcam and USB soundcard) but any attempt at using a flash drive fails. The LEDs on the thumbdrives are lighted, but lsusb does not report that they are connected and they are not automounted. 

I tried these thumbdrives on my laptop which is running exactly the same software and it worked with no problem. 

For the first front port, dmesg reports this:
> 
[13127.408636] usb 4-5: configuration #1 chosen from 1 choice
[13127.466551] scsi562 : SCSI emulation for USB Mass Storage devices
[13127.469814] usb 4-5: USB disconnect, address 27
[13127.470520] usb-storage: device found at 27
[13127.470531] usb-storage: waiting for device to settle before scanning
[13127.711007] usb 4-5: new high speed USB device using ehci_hcd and address 28
[13128.038421] usb 4-5: new high speed USB device using ehci_hcd and address 29
[13128.365909] usb 4-5: new high speed USB device using ehci_hcd and address 30
[13128.885054] usb 4-5: device not accepting address 30, error -71
[13129.180573] usb 4-5: new high speed USB device using ehci_hcd and address 32

And for the second front port:

> [13184.192085] usb 4-6: configuration #1 chosen from 1 choice
[13184.248352] scsi565 : SCSI emulation for USB Mass Storage devices
[13184.253522] usb-storage: device found at 35
[13184.253537] usb-storage: waiting for device to settle before scanning
[13184.806587] usb 4-6: USB disconnect, address 35
[13185.077437] usb 4-6: new high speed USB device using ehci_hcd and address 36
[13185.210476] usb 4-6: configuration #1 chosen from 1 choice
[13185.267005] scsi566 : SCSI emulation for USB Mass Storage devices
[13185.271827] usb-storage: device found at 36
[13185.271847] usb-storage: waiting for device to settle before scanning

Neither seem to work. Any ideas? :(

---

### Post by tamoneya on 2008-08-04
can you try setting your USB ports to USB 1.1 instead of 2.0.  This reduced the transfer speed but it may clear out the errors.  Lets just see if it works and then we can look for a faster solution.

---

### Post by pytheas22 on 2008-08-04
Yes, as tamoneya suggests, try running:
```

sudo rmmod uhci_hcd
sudo rmmod ehci_hcd
sudo modprobe ehci_hcd
```

Then plug the drive in again and see if it works better (this will revert back to USB 1.1 speeds).

Also, have you tried mounting it manually?  You would use a command like:
```

sudo mkdir /media/USB-stick
sudo mount /dev/sdb1 /media/USB-stick
```

Note that you may need to substitute something else for */dev/sdb1* above.  If you don't know how to figure out what to put in there, let me know and I'll explain.

If you get any interesting output from any of these commands, please post.

---

### Post by lucis on 2008-08-07
Running those commands ends up disabling both the USB keyboard and mouse and not re-enabling them until a reboot.


One of the thumbdrives will mount, but goes on and on in an endless loop of mounting and then 5 seconds later unmounting. 

Edit: the thumbdrive works in the back USB port, but not in the front. What's up with that? Could it have something to do with the connection between the front usb ports and the mobo?

---

### Post by pytheas22 on 2008-08-07
> Edit: the thumbdrive works in the back USB port, but not in the front. What's up with that? Could it have something to do with the connection between the front usb ports and the mobo?

Yeah, that explains a lot.  It's probably not a software issue--just a bad connection.  Make sure the cables are connected.  Also sometimes USB buses on the motherboard just go bad.  Unless the drive works in the front port on Windows (if you have it on the same machine), then I don't think this is Ubuntu's fault, but a hardware issue.

---

### Post by lucis on 2008-08-09
> **pytheas22 said:**
> Yeah, that explains a lot.  It's probably not a software issue--just a bad connection.  Make sure the cables are connected.  Also sometimes USB buses on the motherboard just go bad.  Unless the drive works in the front port on Windows (if you have it on the same machine), then I don't think this is Ubuntu's fault, but a hardware issue.

Thanks. I think my friend's just going to get a USB hub and plug it into the back to make it easier. :)

---

