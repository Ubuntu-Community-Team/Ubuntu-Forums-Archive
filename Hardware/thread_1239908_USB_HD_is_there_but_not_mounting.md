---
title: "USB HD is there but not mounting"
date: 2009-08-14
forum: Hardware
---

### Post by vedek on 2009-08-14
Hi guys.

I have a problem with a usb HD i can detect it but not mount it any ideas whats wrong with it.

```
Bus 001 Device 007: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x152d JMicron Technology Corp. / JMicron USA Technology Corp.
  idProduct          0x2338 JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 5 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              6 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

---

### Post by vedek on 2009-08-14
ok guys, i have more info so hopefully i can get this fixed.

i now have a usb icon on the drive thanks to usbmount. but its not letting me mount it 

now i got this result from
```

paddy@paddy-laptop:~$ ls -l /dev/sdb
brw-rw---- 1 root disk 8, 16 2009-08-14 22:46 /dev/sdb
paddy@paddy-laptop:~$ ls -l /dev/sda
brw-rw---- 1 root disk 8, 0 2009-08-14 22:05 /dev/sda
paddy@paddy-laptop:~$ 
```

which i got from 
```
paddy@paddy-laptop:~$ sudo lshw -C disk
SCSI                      
  *-disk           
       description: ATA Disk
       product: SAMSUNG HM160HI
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: HH10
       serial: S1WWJF0S541222
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a6e508e7
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
```

no i am thinking that one is the drive i am looking for this is a netbook so no cd rom drive etc, i think this is a problem that i just don't know enough about to fix it but i am hoping that you guys can help.

---

### Post by jms1989 on 2009-08-14
hmm, try this in your terminal;

run "mount /dev/sdb1 /media/disk" as root. Replace "sdb1" with the hard drive and partition you want to mount and "disk" with what you want to call it.

---

### Post by vedek on 2009-08-15
it still wont mount it is saying unknown partition

---

### Post by jms1989 on 2009-08-15
ok, if you know the partition type, you can include it in your command.

mount -t ext3 /dev/sdb1 /media/disk

For ntfs partitions, replace ext3 with ntfs-3g. For fat32 and fat16, use vfat. If that wont do it, do you mind giving us more info on what we're dealing with?

Please run, "sudo fdisk -l".

---

### Post by vedek on 2009-08-15
once i run the mount part that you suggested i got this message
```

paddy@paddy-laptop:~$ sudo mount -t ntfs-3g /dev/sdb /media/Myfiles
Failed to read bootsector (size=0)
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

fdisk bring up the following

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6e508e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2553    20506941   83  Linux
/dev/sda4            2554       19457   135781380    5  Extended
/dev/sda5            2554       19115   133034202   83  Linux
/dev/sda6           19116       19457     2747083+  82  Linux swap / Solaris
paddy@paddy-laptop:~$ 
```


i hope that helps, i think the data is corrupted but i can see it to format it

---

### Post by jms1989 on 2009-08-15
hmm, i see you are trying to mount the whole disk. Mount can only mount individual partitions.

So try this, sudo mount -t ntfs-3g /dev/sdb1 /media/Myfiles.When mounting, you must specify the disk and the partition number as shown by fdisk -l. Since sda seems to be the main system disk, I assume sdb is your external drive.

---

### Post by vedek on 2009-08-15
```
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
```

is the response i get from that

---

### Post by jms1989 on 2009-08-15
Hmm, from what I gather, it seem as though your partition may be corrupt or missing. Is the disk plugged in and turned on? I didn't see a entry for your external hard drive when you posted the output of fdisk. Please posts the entire output of "sudo fdisk -l". Also, how big is this external disk of yours?

---

### Post by vedek on 2009-08-15
[LEFT]the drive is 70g

and this is the full fdisk
```

paddy@paddy-laptop:~$ sudo fdisk -l
[sudo] password for paddy: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6e508e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2553    20506941   83  Linux
/dev/sda4            2554       19457   135781380    5  Extended
/dev/sda5            2554       19115   133034202   83  Linux
/dev/sda6           19116       19457     2747083+  82  Linux swap / Solaris
```

[/LEFT]

---

### Post by vedek on 2009-08-15
ok i think we might be getting somewhere,

i have been been changing some of the syntax and come up with this

```
paddy@paddy-laptop:~$ sudo mount -t vfat /dev/sdb /media/Myfiles
mount: /dev/sdb: can't read superblock
```

i tried to mount it with sdb1 but it doesn't exist

---

### Post by jms1989 on 2009-08-15
my guess is its not being recognized or is not reporting itself to the os. Have you tried rebooting with the drive plugged in? Also, look in your log files under /var/log/ for any reference to the hard drive. The dmesg, syslog, kernel.log could be worth a look.

Beyond that, I really have no other suggestions other that trying it on another computer to see if its even working. If it fails to mount on another computer, then I'm afraid you may have a dead hard drive. Sorry.

---

### Post by vedek on 2009-08-15
yeah it looks like its cooked shame because it was a nice HD

---

### Post by jms1989 on 2009-08-15
well seeing how its an external disk, try removing it from the enclosure and installing it in a desktop computer. If its fairly new, less than year, it might have a sata interface. Therefore, you need a pc that has a sata power as well as a sata power plug for it. 

Check this out if you don't know what it is: [http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA) and an older disk may have a ide conector, that just looks like a long bar with a bunch of pins (about 40), it takes a standard 40pin connector but you will need to set the junper to master or slave.

So, if that fails. Then, you truly have a dead disk. Sorry for your loss. :(

---

### Post by vedek on 2009-08-15
shame it was a good disk storing everything until the end.:(

---

### Post by vorpalblade on 2009-09-02
I'm having a very similar problem, and have reproduced it with two separate disks on two separate computers.

Both disks worked fine with ubuntu until they were not "safely removed" under windows XP. After being unsafely removed, neither would mount under ubuntu.

fdisk -l indicates that the disk contains a valid vfat partition  at /dev/sdb1, dmesg indicates that the disk was configured and set up as sdb1, however the device /dev/sdb1 does not exist.
/dev/sdb exists, so ubuntu is detecting the disk, but failing to detect the partition.

I've replicated this on jaunty with both a WD Passport and a patriot 8GB thumb drive.

Both disks still mount fine under windows XP. Cleanly removing them under XP does not change their behavior under ubuntu.

I have not been able to find any other reference to this bug besides this thread...perhaps its time for a bug report?

Godspeed

  -Matthew

---

