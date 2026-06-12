---
title: "Ext HDD Mounting =("
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by YinZen on 2005-04-20
Hello there.

Im pretty new to linux  ](*,) and im really stuck trying to mount an external harddrive.
Ive seen all the previous threads on this and tryed the thigs there but it just ont work.
I need help badly.

Thanks to all help =).

---

### Post by alastair on 2005-04-20
When you plug in an external disk (USB/Firewire), the kernel will send a "hotplug" event, and create a device. This device might be /dev/sda1 (say) or something similar. You can then mount the partition(s) on this device somewhere to access it.

To see what device :

With the device not plugged in, open a shell and :

sudo tail -f /var/log/syslog

Plug in the device - and look for kernel messages printed. Anything?

You might see something like :

```

Apr 20 23:54:19 muse kernel: Initializing USB Mass Storage driver...
...
Apr 20 23:54:24 muse kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
...
Apr 20 23:54:25 muse udev[11092]: creating device node '/dev/sda1'

```

This device (as an example) is /dev/sda - with one partition /dev/sda1.

I know the partition has filesystem FAT (vfat), so I can mount it like :

sudo mount -t vfat /dev/sda1 /media/usbdisk

(/media/usbdisk is an existing partition). You can add a similar line to your /etc/fstab file and have the kernel mount automatically when plugged in.

---

### Post by YinZen on 2005-04-21
```
Apr 21 08:47:06 localhost kernel: usb 4-4: new high speed USB device using ehci_hcd and address 4
Apr 21 08:47:06 localhost kernel: scsi1 : SCSI emulation for USB Mass Storage devices
Apr 21 08:47:06 localhost kernel: usb-storage: device found at 4
Apr 21 08:47:06 localhost kernel: usb-storage: waiting for device to settle before scanning
Apr 21 08:47:06 localhost usb.agent[9355]:      usb-storage: already loaded
Apr 21 08:47:11 localhost kernel:   Vendor: Maxtor    Model: 3000LE v01.00.00  Rev: 0100
Apr 21 08:47:11 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 21 08:47:11 localhost kernel: SCSI device sda: 240119808 512-byte hdwr sectors (122941 MB)
Apr 21 08:47:11 localhost kernel: sda: assuming drive cache: write through
Apr 21 08:47:11 localhost kernel: SCSI device sda: 240119808 512-byte hdwr sectors (122941 MB)
Apr 21 08:47:11 localhost kernel: sda: assuming drive cache: write through
Apr 21 08:47:11 localhost kernel:  /dev/scsi/host1/bus0/target0/lun0:
Apr 21 08:47:11 localhost kernel: Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
Apr 21 08:47:11 localhost kernel: usb-storage: device scan complete
Apr 21 08:47:11 localhost scsi.agent[9404]:      sd_mod: loaded sucessfully
Apr 21 08:47:11 localhost udev[9415]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '%k'
Apr 21 08:47:11 localhost udev[9415]: creating device node '/dev/sda'

``` is what i get when i do the first thing you said... i will try th eother later.  Hope this helps.

---

### Post by alastair on 2005-04-21
Your logs :

```

Apr 21 08:47:11 localhost udev[9415]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '%k'
Apr 21 08:47:11 localhost udev[9415]: creating device node '/dev/sda'

```

After this last line, you should also see something like :

```

configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda1' becomes '%k'
creating device node '/dev/sda1'

```

i.e. the disk /dev/sda --> the partition /dev/sda1

You can see what partitions are on the disk using :

sudo fdisk -l /dev/sda

and mount one of them e.g. /dev/sda1.

---

### Post by YinZen on 2005-04-21
all i get when i do sudo fdisk -l /dev/sda is:

```
Disk /dev/sda: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by lorap on 2005-04-22
hi friend!
try this,maybe it'd help:

1.create any directory,say usb:

mkdir /home/yourusername.usb

2.connect to usbhd:

sudo mount /de/sda0 /home/yourusername/usb -t vfat -o umask=000

p.s.:
if it says the device's busy try sda1 or even sda2.
if your fs's ntfs then change vfat to ntfs.
have a nice day!
pavel

---

### Post by tUrtleAE86 on 2005-04-23
I've been having problems mounting my USB hard drive too..
It's a FAT32 drive, formatted using Partition Magic in Windows XP.

"fdisk -l /dev/sdc" shows:
```

Disk /dev/sdc: 200.0 GB, 200049648128 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24321   195358428   54  OnTrackDM6

```

"sudo mount -t vfat /dev/sdc1 /mnt/usb" and
"sudo mount /dev/sdc1 /mnt/usb -t vfat -o umask=000" end up with:
```

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

"dmesg | tail" shows:
```

  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sde at scsi6, channel 0, id 0, lun 1
usb-storage: device scan complete
FAT: invalid media value (0x7c)
VFS: Can't find a valid FAT filesystem on dev sdc1.
FAT: invalid media value (0x7c)
VFS: Can't find a valid FAT filesystem on dev sdc1.
VFS: Can't find a HFS filesystem on dev loop0.
FAT: invalid media value (0x7c)
VFS: Can't find a valid FAT filesystem on dev sdc1.

```

I'm not really sure if "OnTrackDM6" means anything significant. Nor do I have any idea where else to go with this.  :confused:
Any ideas?

-- Partitioned and formatted in linux, and the drive works great now.  :)

---

### Post by XplOzIOn on 2005-05-08
[QUOTE=tUrtleAE86]I've been having problems mounting my USB hard drive too..
It's a FAT32 drive, formatted using Partition Magic in Windows XP.

"fdisk -l /dev/sdc" shows:
```

Disk /dev/sdc: 200.0 GB, 200049648128 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24321   195358428   54  OnTrackDM6

```

"sudo mount -t vfat /dev/sdc1 /mnt/usb" and
"sudo mount /dev/sdc1 /mnt/usb -t vfat -o umask=000" end up with:
```

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

"dmesg | tail" shows:
```

  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sde at scsi6, channel 0, id 0, lun 1
usb-storage: device scan complete
FAT: invalid media value (0x7c)
VFS: Can't find a valid FAT filesystem on dev sdc1.
FAT: invalid media value (0x7c)
VFS: Can't find a valid FAT filesystem on dev sdc1.
VFS: Can't find a HFS filesystem on dev loop0.
FAT: invalid media value (0x7c)
VFS: Can't find a valid FAT filesystem on dev sdc1.

```

I'm not really sure if "OnTrackDM6" means anything significant. Nor do I have any idea where else to go with this.  :confused:
Any ideas?

-- Partitioned and formatted in linux, and the drive works great now.  :)[/QUOTE]


Yeah that happends when partitioning with Part Magic, i had same problem with an hdd

---

