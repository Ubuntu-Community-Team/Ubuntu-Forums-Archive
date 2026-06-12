---
title: "Problems automounting USB devices"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by Musagetes on 2005-05-30
Hello.

I'm relatively new to linux, so I'm having problems troubleshooting this issue I have when plugging in my MP3 player, and I was hoping some of you could help me out.

I was under the impression that linux didn't require any drivers for USB devices, or at least external USB discs, such as digital cameras and MP3 players. But when I insert my MP3 player nothing seems to happen. I can view it with 'usbview', although it does seem to connect and disconnect with no end. And therefore I tried tailing my logs:

> [hn@museion > ~]$ sudo tail -f /var/log/messages
May 30 13:04:16 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 04
May 30 13:04:16 localhost kernel: SCSI device sda: 499712 512-byte hdwr sectors (256 MB)
May 30 13:04:16 localhost kernel: sda: Write Protect is off
May 30 13:04:16 localhost kernel: SCSI device sda: 499712 512-byte hdwr sectors (256 MB)
May 30 13:04:16 localhost kernel: sda: Write Protect is off
May 30 13:04:16 localhost kernel:  /dev/scsi/host13/bus0/target0/lun0:SCSI error : <13 0 0 0> return code = 0x70000
May 30 13:04:16 localhost kernel: end_request: I/O error, dev sda, sector 0
May 30 13:04:16 localhost kernel: usb 5-3: USB disconnect, address 18
May 30 13:04:31 localhost hal.hotplug[23581]: timout(10000 ms) waiting for /devices/pci0000:00/0000:00:1d.7/usb5/5-3/5-3:1.0/host13/target13:0:0/13:0:0:0
May 30 13:04:41 localhost scsi.agent[23693]: Attribute /sys/devices/pci0000:00/0000:00:1d.7/usb5/5-3/5-3:1.0/host13/target13:0:0/13:0:0:0/type does not exist
I can tell that something is wrong, but I have no idea what ... I've edited my fstab with the following:
/dev/sda        /mnt/player     vfat    auto,defaults   0       0

What am I doing wrong?

---

### Post by Mez on 2005-05-30
looks like you're trying to mount a whole hard drive... which isnt ight, you need to mount the partition

/dev/sda1 is what you should be looking for ... methinks

---

