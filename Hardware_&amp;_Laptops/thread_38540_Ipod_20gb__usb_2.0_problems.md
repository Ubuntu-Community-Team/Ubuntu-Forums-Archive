---
title: "Ipod 20gb / usb 2.0 problems"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by elatomo on 2005-05-31
Hi!

A few days ago i bought one 20gb ipod and since then i'm stuck trying to set it up on my linux box. The ipod is formatted in windows and works fine there, but when connected to my ubuntu with a usb 2.0 port (i'm using a brand new conceptronics pci usb 2.0 card) i can't get it mounted.

The usb modules seems to be loaded without problems... A "lsmod | grep usb" returns this:

```
usb_storage 64064 1
scsi_mod 119936 2 usb_storage,sd_mod
usbcore 107384 5 usb_storage,ehci_hcd,ohci_hcd,uhci_hcd
ide_core 118988 5 usb_storage,ide_cd,ide_generic,via82cxxx,ide_disk
```

These are the errors returned by dmesg and mount:

```
sudo mount -t vfat /dev/sda2 /media/ipod
mount: /dev/sda2: cannot read superblock
```

```
[...]
usb 6-3: new high speed USB device using ehci_hcd and address 5
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
Vendor: Apple Model: iPod Rev: 1.62
Type: Direct-Access ANSI SCSI revision: 00
SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
sda : READ CAPACITY failed.
sda : status=0, message=00, host=7, driver=00
sda : sense not available.
sda: Write Protect is off
sda: Mode Sense: 00 00 00 00
sda: assuming drive cache: write through
/dev/scsi/host2/bus0/target0/lun0:SCSI error : <2 0 0 0> return code = 0x70000
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
SCSI error : <2 0 0 0> return code = 0x70000
end_request: I/O error, dev sda, sector 1
Buffer I/O error on device sda, logical block 1
SCSI error : <2 0 0 0> return code = 0x70000
end_request: I/O error, dev sda, sector 2
Buffer I/O error on device sda, logical block 2
SCSI error : <2 0 0 0> return code = 0x70000
[...]

```


Searching for info in google about the buffer i/o error i found one issue with some 4g ipods. The problem is related with the CONFIG_EFI_PARTITION feature being enabled in the kernel configuration ([http://www.linuxquestions.org/questions/showthread.php?postid=1197015#post1197015)](http://www.linuxquestions.org/questions/showthread.php?postid=1197015#post1197015)), but my kernel has that feature disabled...  ](*,) 

My kernel version is 2.6.10-7 (386 deb) and my linux restricted modules version is 2.6.10.5-1.

Thanks in advance and sorry for my (really) poor english!

---

### Post by elatomo on 2005-06-01
Finally i've managed to automount the ipod, the problem seemed to be with the scsi_mod, which (i think) wasn't loaded correctly. I've added that module to the /etc/modules file and now, after connecting the ipod to the computer it's automounted in /media/IPOD.

The problem now is i can't sync the ipod with gtkpod. I've set the mount point in the program to /media/IPOD and the id3 charset to ISO-8859-1 (easytag recommends it),

These are the errors i get:

- dmesg returns this when trying to sync the ipod with gtkpod:

```
FAT: Filesystem panic (dev sda2)
    fat_get_cluster: invalid cluster chain (i_pos 0)
FAT: Filesystem panic (dev sda2)
    fat_get_cluster: invalid cluster chain (i_pos 0)
SCSI error : <0 0 0 0> return code = 0x70000
end_request: I/O error, dev sda, sector 156509
FAT: Directory bread(block 76184) failed
FAT: Filesystem panic (dev sda2)
    fat_get_cluster: invalid cluster chain (i_pos 0)
```

- gtkpod returns this:

```
Could not open file "/media/IPOD/iPod_Control/Music/f19/gtkpod00057.mp3" for writing.
Could not open file "/media/IPOD/iPod_Control/Music/f00/gtkpod00058.mp3" for writing.
Could not open file "/media/IPOD/iPod_Control/Music/f01/gtkpod00059.mp3" for writing.
...
```

I don't know if it could be a charset issue (the iocharset is set to utf8), after automonting the ipod, my /etc/mtab look like this:

```
/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hdd5 /media/circulodos ext3 rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda2 /media/IPOD vfat rw,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```



Thanks in advance!

---

