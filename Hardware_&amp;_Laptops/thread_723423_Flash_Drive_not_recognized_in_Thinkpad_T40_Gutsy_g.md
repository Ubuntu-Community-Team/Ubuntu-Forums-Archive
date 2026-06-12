---
title: "Flash Drive not recognized in Thinkpad T40 Gutsy gibbon"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by rakusson on 2008-03-13
hi, I upgraded ubuntu 7.04 to 7.10, however, now my system does not recognize my usb drive that used to recognize previously!! The same USB drive is recognized by WinXP. Interesting thing is that, my USB mouse works perfectly with Ubuntu 7.10.

this is my FSTAB file
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

Here is the result of dmesg | grep -i usb 
```

dmesg | grep -i usb
[   16.596541] usbcore: registered new interface driver usbfs
[   16.596593] usbcore: registered new interface driver hub
[   16.596654] usbcore: registered new device driver usb
[   16.600393] USB Universal Host Controller Interface driver v3.0
[   16.600807] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   16.601159] usb usb1: configuration #1 chosen from 1 choice
[   16.601228] hub 1-0:1.0: USB hub found
[   16.705821] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   16.706119] usb usb2: configuration #1 chosen from 1 choice
[   16.706187] hub 2-0:1.0: USB hub found
[   16.808961] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   16.809260] usb usb3: configuration #1 chosen from 1 choice
[   16.809330] hub 3-0:1.0: USB hub found
[   16.914350] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   16.918328] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.918535] usb usb4: configuration #1 chosen from 1 choice
[   16.918605] hub 4-0:1.0: USB hub found


```

I tried very hard to find a solution to this problem, however, failed to do so. This is the only reason I had to log into my shitty windows to copy files from or to USB disk  (I hate that). Please help me.

---

### Post by rakusson on 2008-03-21
It is sad that I have not found any reply yet. plz someone help me.

---

