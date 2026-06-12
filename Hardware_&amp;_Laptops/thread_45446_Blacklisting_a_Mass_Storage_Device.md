---
title: "Blacklisting a Mass Storage Device"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-06-30
Hello,

    I'm trying to get my TiVX to connect under VMWare, but it seems that Linux takes control of it before Windows (under VMWare) gets a chance to. The TiVX is simply a hard drive that connects as a mass storage device using USB under Linux. What do I need to add to /etc/hotplug/blacklist in order to prevent Linux from loading it? And is there a way to do it so only the TiVX is blacklisted and not my other USB key drives? If not, I'm fine blacklisting it all, I'll just edit the file each time I connect the TiVX...

If it helps, here's some output from /var/log/messages when I connect it:

```

Jun 30 06:30:54 localhost kernel: usb 5-3.2: new high speed USB device using ehci_hcd and address 11
Jun 30 06:30:54 localhost kernel: scsi5 : SCSI emulation for USB Mass Storage devices
Jun 30 06:30:55 localhost usb.agent[18248]:      usb-storage: already loaded
Jun 30 06:31:02 localhost kernel:   Vendor: Maxtor    Model: 6B250R0           Rev: BAH4
Jun 30 06:31:02 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Jun 30 06:31:02 localhost kernel: SCSI device sde: 490234752 512-byte hdwr sectors (251000 MB)
Jun 30 06:31:02 localhost kernel: SCSI device sde: 490234752 512-byte hdwr sectors (251000 MB)
Jun 30 06:31:02 localhost kernel:  /dev/scsi/host5/bus0/target0/lun0: p1
Jun 30 06:31:02 localhost kernel: Attached scsi disk sde at scsi5, channel 0, id 0, lun 0
Jun 30 06:31:02 localhost scsi.agent[18313]:      sd_mod: loaded sucessfully
Jun 30 06:31:07 localhost kernel: NTFS volume version 3.1.
Jun 30 06:31:25 localhost kernel: usb 5-3.2: USB disconnect, address 11

``` 

Thanks...  :-P

---

### Post by audax321 on 2005-06-30
Never mind, I figured it out. I just blacklisted usb-storage and it worked. Of course now I have to rmmod usb-storage and then blacklist it every time I want to copy stuff to the TiVX but I can write to an NTFS hard drive through VMWare now, so I guess its worth it...  :)

---

