---
title: "External firewire drive not recognized"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by wgscott on 2005-07-25
Sorry if this gets asked a lot, but I am new to Ubuntu (as of Friday evening) and my searching hasn't turned up anything definitive.

I have an external firewire hard drive that I want to plug in and have recognized.  I'm new to linux and the kernel stuff is unfamiliar territory (my familiarity is with OS X, bsd, irix and so on).  The drive is HFS+ and I have installed the relevant debian packages for that filesystem, but I don't think the device is even being recognized -- I haven't got the the point of trying to mount it unsuccessfully.

Any pointers?

---

### Post by wgscott on 2005-07-26
The same drive also has USB ports, so I tried instead with USB and got a little bit further.  In /var/log/syslog, there are entries when I plug in the drive with USB.  In contrast, nothing happens with the firewire when I plug it in.  I also tried plugging it in and rebooting, but that didn't help for the firewire either.

Returning to the USB mode, I get the following 
 
```

Jul 26 12:38:14 localhost kernel:   Vendor: ST340083  Model: 2A                Rev:  0 0
Jul 26 12:38:14 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul 26 12:38:14 localhost kernel: SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
Jul 26 12:38:14 localhost kernel: sdc: assuming drive cache: write through
Jul 26 12:38:14 localhost kernel: SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
Jul 26 12:38:14 localhost kernel: sdc: assuming drive cache: write through
Jul 26 12:38:14 localhost kernel:  /dev/scsi/host4/bus0/target0/lun0: [mac] p1 p2 p3 p4
Jul 26 12:38:14 localhost kernel: Attached scsi disk sdc at scsi4, channel 0, id 0, lun 0
Jul 26 12:38:14 localhost kernel: usb-storage: device scan complete
Jul 26 12:38:14 localhost scsi.agent[9343]:      sd_mod: loaded sucessfully
Jul 26 12:38:14 localhost udev[9353]: configured rule in '/etc/udev/rules.d/udev.rules' at line 28 applied, 'sdc' becomes '%k'
Jul 26 12:38:14 localhost udev[9353]: creating device node '/dev/sdc'
Jul 26 12:38:14 localhost udev[9397]: configured rule in '/etc/udev/rules.d/udev.rules' at line 28 applied, 'sdc1' becomes '%k'
Jul 26 12:38:14 localhost udev[9397]: creating device node '/dev/sdc1'
Jul 26 12:38:14 localhost udev[9424]: configured rule in '/etc/udev/rules.d/udev.rules' at line 28 applied, 'sdc2' becomes '%k'
Jul 26 12:38:14 localhost udev[9424]: creating device node '/dev/sdc2'
Jul 26 12:38:14 localhost udev[9451]: configured rule in '/etc/udev/rules.d/udev.rules' at line 28 applied, 'sdc3' becomes '%k'
Jul 26 12:38:14 localhost udev[9451]: creating device node '/dev/sdc3'
Jul 26 12:38:14 localhost udev[9478]: configured rule in '/etc/udev/rules.d/udev.rules' at line 28 applied, 'sdc4' becomes '%k'
Jul 26 12:38:14 localhost udev[9478]: creating device node '/dev/sdc4'
Jul 26 12:38:15 localhost kernel: HFS+-fs: failed to load catalog file
Jul 26 12:38:15 localhost kernel: HFS+-fs: unable to find HFS+ superblock
Jul 26 12:39:18 localhost kernel: HFS+-fs: unable to find HFS+ superblock
Jul 26 12:39:26 localhost kernel: HFS+-fs: unable to find HFS+ superblock
Jul 26 12:39:32 localhost kernel: HFS+-fs: failed to load catalog file
Jul 26 12:39:38 localhost kernel: attempt to access beyond end of device
Jul 26 12:39:38 localhost kernel: sdc1: rw=0, want=262211, limit=63
Jul 26 12:39:38 localhost kernel: HFS+-fs: unable to find HFS+ superblock
Jul 26 12:39:49 localhost kernel: HFS+-fs: failed to load catalog file
Jul 26 12:41:15 localhost udev[9662]: removing device node '/dev/sdc4'
Jul 26 12:41:15 localhost udev[9677]: removing device node '/dev/sdc3'
Jul 26 12:41:15 localhost udev[9692]: removing device node '/dev/sdc2'
Jul 26 12:41:15 localhost udev[9707]: removing device node '/dev/sdc1'
Jul 26 12:41:15 localhost udev[9722]: removing device node '/dev/sdc'
Jul 26 12:41:15 localhost kernel: usb 5-8: USB disconnect, address 3 

```



Some of these are responses to me trying to mount partitions manually. 

The error message for one of the partitions, which I think is the one I should be mounting, is

Jul 26 12:39:32 localhost kernel: HFS+-fs: failed to load catalog file


I don't know what a catalog file is.

---

