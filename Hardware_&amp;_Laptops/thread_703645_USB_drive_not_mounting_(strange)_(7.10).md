---
title: "USB drive not mounting (strange) (7.10)"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by rakusson on 2008-02-21
hi,

When I insert my USB drive, nothing happens. Then I tried to mount it manually. I was surprised to find this in my /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6f6c8417-a940-46d9-b896-4f8e9e6d1d35 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8C49000C48FFF2B6 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=04582BB4582BA380 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=24E03B64E03B3AFE /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=BC04568904564694 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=1112-0BE5  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=022cc1bf-3369-48a7-9f24-5a758022615e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

Then I did
$ dmesg | tail -20
```

[ 4142.852000] usb 4-3: new high speed USB device using ehci_hcd and address 65
[ 4143.112000] ehci_hcd 0000:00:1d.7: port 3 reset error -110
[ 4143.112000] hub 4-0:1.0: hub_port_status failed (err = -32)
[ 4143.952000] usb 4-3: new high speed USB device using ehci_hcd and address 67
[ 4145.192000] usb 4-3: new high speed USB device using ehci_hcd and address 73
[ 4145.452000] ehci_hcd 0000:00:1d.7: port 3 reset error -110
[ 4145.452000] hub 4-0:1.0: hub_port_status failed (err = -32)
[ 4148.924000] usb 4-3: new high speed USB device using ehci_hcd and address 89
[ 4153.548000] usb 4-3: new high speed USB device using ehci_hcd and address 113
[ 4154.788000] usb 4-3: new high speed USB device using ehci_hcd and address 119
[ 4155.276000] usb 4-3: new high speed USB device using ehci_hcd and address 121
[ 4163.472000] usb 4-3: new high speed USB device using ehci_hcd and address 38
[ 4169.036000] usb 4-3: new high speed USB device using ehci_hcd and address 67
[ 4171.216000] usb 4-3: new high speed USB device using ehci_hcd and address 78
[ 4172.292000] usb 4-3: new high speed USB device using ehci_hcd and address 83
[ 4174.660000] usb 4-3: new high speed USB device using ehci_hcd and address 95
[ 4174.920000] ehci_hcd 0000:00:1d.7: port 3 reset error -110
[ 4174.920000] hub 4-0:1.0: hub_port_status failed (err = -32)
[ 4175.760000] usb 4-3: new high speed USB device using ehci_hcd and address 97
[ 4178.128000] usb 4-3: new high speed USB device using ehci_hcd and address 109

```
what should I do to mount my usb drive?

---

### Post by rakusson on 2008-02-22
:confused::confused: No reply yet.

---

### Post by evan.rotert on 2008-06-26
I had a similar problem with my Sandisk Sansa Fuze MP3 player.  I found a solution here:

[https://answers.launchpad.net/ubuntu/+question/4272](https://answers.launchpad.net/ubuntu/+question/4272)

Try 'sudo modprobe -r ehci_hcd'

Hope this helps!  I'm gonna try blacklisting this module so I don't have to deal with it every time I reboot.  We'll see if that breaks things or fixes them :-)

---

### Post by evan.rotert on 2008-06-26
Ok, so after a bit more reading I've come to understand that this module is responsible for USB 2.0 support.  Therefore, if you remove it (as that command will do) you USB devices should all still work, but only at USB 1.1 speed (not too fast...).  If anyone has a solution for this problem that retains full USB 2.0 speed, I'd love to hear it!

---

