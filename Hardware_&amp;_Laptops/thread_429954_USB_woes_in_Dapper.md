---
title: "USB woes in Dapper"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by v4169sgr on 2007-05-01
Hello! I have an issue which seems to affect one USB removable storage device recently purchased, and none others that I know of.

I can insert the USB key, auto mount it, and invoke konqueror pointing at the correct location. I can copy a file(s) over to the key. But 'safely remove' does not work, and if the USB key is pulled [after an interval] then reinserted, the files are not there.

I am running Kubuntu 6.06 with a 2.6.15 series kernel.

$ uname -a
Linux [host] 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

$ lsusb
Bus 002 Device 012: ID 0204:6025

Result of tail -f /var/log/messages through the repro steps above:

```

May  1 22:51:51 localhost kernel: [17187965.464000] usb 2-7: new high speed USB device using ehci_hcd and address 11
May  1 22:51:51 localhost kernel: [17187965.596000] scsi8 : SCSI emulation for USB Mass Storage devices
May  1 22:51:56 localhost kernel: [17187970.596000]   Vendor: NETAC     Model: USB2.0 FlashDisk  Rev: 4.00
May  1 22:51:56 localhost kernel: [17187970.596000]   Type:   Direct-Access                      ANSI SCSI revision: 02
May  1 22:51:56 localhost kernel: [17187970.596000] SCSI device sdb: 1997055 2048-byte hdwr sectors (4090 MB)
May  1 22:51:56 localhost kernel: [17187970.600000] SCSI device sdb: 1997055 2048-byte hdwr sectors (4090 MB)
May  1 22:51:56 localhost kernel: [17187970.600000]  sdb: sdb1
May  1 22:51:56 localhost kernel: [17187970.600000] sd 8:0:0:0: Attached scsi disk sdb
May  1 22:51:56 localhost kernel: [17187970.600000] sd 8:0:0:0: Attached scsi generic sg1 type 0
May  1 22:52:00 localhost kernel: [17187974.376000] UDF-fs: No partition found (1)
May  1 22:52:01 localhost kernel: [17187974.904000] UDF-fs: No partition found (1)
May  1 22:52:01 localhost kernel: [17187974.996000] Unable to identify CD-ROM format.
May  1 22:52:01 localhost kernel: [17187975.088000] Unable to identify CD-ROM format.
May  1 22:52:39 localhost kernel: [17188013.192000] usb 2-7: reset high speed USB device using ehci_hcd and address 11
May  1 22:53:09 localhost kernel: [17188043.436000] usb 2-7: reset high speed USB device using ehci_hcd and address 11
May  1 22:53:20 localhost kernel: [17188053.680000] usb 2-7: reset high speed USB device using ehci_hcd and address 11
May  1 22:53:20 localhost kernel: [17188053.928000] usb 2-7: reset high speed USB device using ehci_hcd and address 11
May  1 22:53:30 localhost kernel: [17188064.172000] usb 2-7: reset high speed USB device using ehci_hcd and address 11
May  1 22:53:30 localhost kernel: [17188064.304000] sd 8:0:0:0: scsi: Device offlined - not ready after error recovery
May  1 22:53:30 localhost kernel: [17188064.304000] sd 8:0:0:0: SCSI error: return code = 0x50000
May  1 22:53:30 localhost kernel: [17188064.304000] end_request: I/O error, dev sdb, sector 5264
May  1 22:53:30 localhost kernel: [17188064.304000] lost page write due to I/O error on sdb1
May  1 22:53:30 localhost last message repeated 9 times
May  1 22:53:30 localhost kernel: [17188064.304000] sd 8:0:0:0: SCSI error: return code = 0x10000
May  1 22:53:30 localhost kernel: [17188064.304000] end_request: I/O error, dev sdb, sector 5504
May  1 22:54:25 localhost kernel: [17188119.448000] usb 2-7: USB disconnect, address 11

```


Result of tail -f /var/log/messages for a USB key that works without a hitch:

```
May  1 22:13:35 localhost kernel: [17185669.492000] usb 2-7: new high speed USB device using ehci_hcd and address 4
May  1 22:13:36 localhost kernel: [17185669.636000] scsi5 : SCSI emulation for USB Mass Storage devices
May  1 22:13:41 localhost kernel: [17185674.636000]   Vendor:           Model: USB Flash Memory  Rev: 1.04
May  1 22:13:41 localhost kernel: [17185674.636000]   Type:   Direct-Access                      ANSI SCSI revision: 00
May  1 22:13:42 localhost kernel: [17185675.640000] SCSI device sdb: 1001472 512-byte hdwr sectors (513 MB)
May  1 22:13:42 localhost kernel: [17185675.640000] sdb: Write Protect is off
May  1 22:13:42 localhost kernel: [17185675.648000] SCSI device sdb: 1001472 512-byte hdwr sectors (513 MB)
May  1 22:13:42 localhost kernel: [17185675.648000] sdb: Write Protect is off
May  1 22:13:42 localhost kernel: [17185675.648000]  sdb: sdb1
May  1 22:13:42 localhost kernel: [17185675.652000] sd 5:0:0:0: Attached scsi removable disk sdb
May  1 22:13:42 localhost kernel: [17185675.652000] sd 5:0:0:0: Attached scsi generic sg1 type 0
May  1 22:13:45 localhost kernel: [17185678.564000] UDF-fs: No partition found (1)
May  1 22:13:45 localhost kernel: [17185678.600000] UDF-fs: No partition found (1)
May  1 22:13:45 localhost kernel: [17185678.692000] Unable to identify CD-ROM format.
May  1 22:13:45 localhost kernel: [17185678.784000] Unable to identify CD-ROM format.
May  1 22:15:24 localhost kernel: [17185778.368000] usb 2-7: USB disconnect, address 4

```

I have tried reformatting the suspect key within both Linux and Windows, to no avail. The problem persists. Can anyone explain why the issue is happening, and what can be done about it?

---

### Post by v4169sgr on 2007-05-02
*bump*

---

### Post by jjordan on 2007-05-03
I used to have similar problems under Edgy.  I eventually figured out that it was just writting very very slowly.  Copy a small file and let it set for several minutes and then try to "Safely Remove."  

I believe the issue is caused by write caching.

BTW, Fiesty does NOT have this issue.  I copy a 48MB video file over every morning to watch the news on the bus and it works pretty much instantly.

-j

---

### Post by v4169sgr on 2007-05-03
Thanks very much for your reply.

I tried the device in a windows machine, and it did not work there either. So it turns out that it is a hardware issue.

Ah well:(

---

