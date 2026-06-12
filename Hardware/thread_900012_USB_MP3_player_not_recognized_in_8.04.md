---
title: "USB MP3 player not recognized in 8.04"
date: 2008-08-24
forum: Hardware
---

### Post by Old Fart on 2008-08-24
My mp3 player, a Sansa Clip  works well in Kubuntu 7.10 . Its seen as a usb drive and the battery charges properly. But ever since I installed Kubuntu 8.04 it's not recognized as a drive and it wont charge. Whenever I plug the device in the following entries are appended to dmesg

[  112.485267] usb 7-2: new high speed USB device using ehci_hcd and address 4
[  113.593733] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[  113.593739] hub 7-0:1.0: hub_port_status failed (err = -32)

What does this mean?  How can I fix this?

---

### Post by Crafty Kisses on 2008-08-25
Post the following output of > lsusb

---

### Post by Old Fart on 2008-08-25
Here is the output of lsusb

Bus 007 Device 003: ID 04a9:221c Canon, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 004: ID 046d:c513 Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Canon is my scanner and logitech is my mouse/keyboard so the sansa doesn't show up.

---

### Post by bubieyehyeh on 2008-08-30
> **Old Fart said:**
> My mp3 player, a Sansa Clip  works well in Kubuntu 7.10 . Its seen as a usb drive and the battery charges properly. But ever since I installed Kubuntu 8.04 it's not recognized as a drive and it wont charge. Whenever I plug the device in the following entries are appended to dmesg

[  112.485267] usb 7-2: new high speed USB device using ehci_hcd and address 4
[  113.593733] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[  113.593739] hub 7-0:1.0: hub_port_status failed (err = -32)

What does this mean?  How can I fix this?

No idea what the problem is but I've found two work arounds. Since I get the same error messages.

1) Try lsusb several times, if it suddenly appears in the lsusb output it will usually appear as a desktop item a few seconds later.

2) Disable and enable USB2 kernel module with "sudo modprobe -r ehci_hcd; sudo modprobe echi_hcd". It then appears as a desktop icon immediately for me each time.

2) has always worked, 1) is quicker to do, but I've only just discovered so I'm not sure what its success ratio is longterm, but so 100% after 2 or 3 lsusb's.

More info in launchpad bug 231049.

Hope thats some helps.

---

### Post by Old Fart on 2008-08-31
Thanks bubieyehyeh

I checked out the bug report at launchpad which pointed me to this thread  [http://ubuntuforums.org/showthread.php?t=790517&highlight=sansa+clip](http://ubuntuforums.org/showthread.php?t=790517&highlight=sansa+clip) which had the answer I've bee looking for. As it turns out all I had to do was change the usb mode form auto detect to msc. Thanks again for steering me in the right direction.:biggrin:

---

