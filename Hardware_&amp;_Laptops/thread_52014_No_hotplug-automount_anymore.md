---
title: "No hotplug-automount anymore?"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by entner on 2005-07-26
When I plug my iPod Shuffle on the USB port usually a new device is created in /dev/sdx and mounted to /mount/something. This does not work anymore as there seems to be a problem with hotplugging.

My kernel:
Linux in5 2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686 GNU/Linux

It seems that the following, missing line in **/var/log/messages** which I found on a working system is the reason:
```
Jul 25 18:32:58 localhost scsi.agent[7984]:      sd_mod: loaded sucessfully
``` 

And here the **/var/log/messages** after plugging the iPod:
```
Jul 26 11:42:00 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 3
Jul 26 11:42:00 localhost kernel: usb 4-3: configuration #1 chosen from 2 choices
Jul 26 11:42:00 localhost kernel: scsi9 : SCSI emulation for USB Mass Storage devices
Jul 26 11:42:05 localhost kernel:   Vendor: Apple     Model: iPod              Rev: 2.70
Jul 26 11:42:05 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 04
Jul 26 11:42:05 localhost kernel: SCSI device sdb: 2032640 512-byte hdwr sectors (1041 MB)
Jul 26 11:42:05 localhost kernel: sdb: Write Protect is off
Jul 26 11:42:05 localhost kernel: SCSI device sdb: 2032640 512-byte hdwr sectors (1041 MB)
Jul 26 11:42:05 localhost kernel: sdb: Write Protect is off
Jul 26 11:42:05 localhost kernel:  /dev/scsi/host9/bus0/target0/lun0: p1
Jul 26 11:42:05 localhost kernel: Attached scsi removable disk sdb at scsi9, channel 0, id 0, lun 0
``` 

Any clues why hotplug doesn't call this scsi.agent? I tried to restart /etc/init.d/hotplug, didn't help though.

Manually mounting the device in /.dev/sdx does work btw.

Thanks,
Burt

-- 
[http://www.entner.net/](http://www.entner.net/)

---

