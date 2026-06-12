---
title: "Firewire not working"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by wr0x2 on 2006-06-04
Running breezy 5.10 with default kernel. Firewire has always worked for me, and I have always used it to mount my ipod. Today, I was playing with an old firewire hdd enclosure I have, and got a drive to mount with it. Somewhere after that, firewire stopped working. I can't mount a 250GB drive in another enclosure that I had working earlier, and although my ipod charges, it won't mount. Here's what happens after I plug in my ipod:
```

wr0x2@USSENTERPRISE:~$ dmesg | tail
[4295507.282000] scsi8 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4295528.484000] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[4295528.485000] sbp2: probe of 0090a9500000f744-0 failed with error -16
[4295537.386000] ieee1394: Error parsing configrom for node 0-00:1023
[4295537.386000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0090a9500000f744]
[4295540.692000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4295744.360000] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[000a2700029a8be4]
[4295744.360000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[4295744.617000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4295744.617000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023

```

This is what happens when any other firewire device is plugged in, in particular the "[4295744.360000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting..." error.

---

### Post by macabro22 on 2007-12-22
bump

---

