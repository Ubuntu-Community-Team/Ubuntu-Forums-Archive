---
title: "Firewire DVD writer problem."
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by jml75 on 2005-04-08
Hi, I have a problem with my firewire dvd writer.
If I plug it in when ubuntu if started, it detects it and works just fine.

Then if I disconnect it or turn it of and reconnect it, nothing is happening.

I dont' have the dmesg output now but I'll post it when I'll be home in an hour.

It's as if the firewire bus stals after the disconnection. It will only work if I restart the computer.

Any Ideas?

---

### Post by jml75 on 2005-04-08
Also, it does not do that in Debian...

It did that bug in Warty to but in debian, I can disconnect it and reconnect it no problem.

Can't figure it out.

---

### Post by jml75 on 2005-04-09
Here is the dmesg I got.

ieee1394: Error parsing configrom for node 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0030e0025010360e]
scsi2 : SCSI emulation for IEEE-1394 SBP-2 Devices
ieee1394: sbp2: Logged into SBP-2 device
ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
  Vendor: PLEXTOR   Model: DVDR   PX-716A    Rev: 1.04
  Type:   CD-ROM                             ANSI SCSI revision: 02
sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi2, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi2, channel 0, id 0, lun 0,  type 5
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0030e0025010360e]

After the node suspended, nothing hapens.

---

