---
title: "4G iPod not mountable"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by mjanssen on 2005-05-09
I can't mount my 4G iPod. The problem is that it worked last week when I was using FC3 and it even worked two days ago right after I finished installing Hoary. It still works fine when I hook it up to my XP box, but when I hook it up to Hoary, dmesg says:
```
usb 4-5: new high speed USB device using ehci_hcd and address 4
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
sdb: Write Protect is off
sdb: Mode Sense: 64 00 00 08
sdb: assuming drive cache: write through
SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
sdb: Write Protect is off

```

But nothing happens. Just two days ago, in the same system, the /media/SCOOBY folder would pop up and the drive would appear on my desktop. Now nothing happens. I tried adding the following line to /etc/fstab:

```
/dev/sdb	/media/SCOOBY	vfat	rw,user,noauto	0	0
```

This allows the Apple iPod to appear under the Computer, but when I try to mount it, it returns the following error:
> mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so 

dmesg | tail shows
```
FAT: invalid media value (0x00)
VFS: Can't find a valid FAT filesystem on dev sdb.
```

But yet it still works under Windows.

This is very frustrating, because it has worked. I had backed all my music up to the iPod and I was able to transfer all 9GB off just two days ago onto my otherwise-wonderful Hoary system. Are there any conflicts I could introduce? I've been installing software like mad via Synaptic (graveman didn't work for cd-burning so I installed k3b), but I didn't start monkeying with /etc/fstab until it quit mounting. That's not something I wanted to do, because it should be hotplugging, so I just got frustrated.

Anyone?

---

### Post by 23meg on 2005-05-09
this is not a mac formatted ipod by any chance, is it?

try this in your fstab:

```
/dev/sdb /media/SCOOBY vfat defaults,user,noauto,sync,umask=000 0 0
```

---

### Post by mjanssen on 2005-05-09
No, it's a windows-formatted iPod.

When I got it, I hooked it up to a friend's Windows machine to update it and format it.

---

### Post by 23meg on 2005-05-09
also try ejecting the ipod (sudo eject /dev/sdb), commenting out / removing the ipod line on fstab, and rebooting.

---

