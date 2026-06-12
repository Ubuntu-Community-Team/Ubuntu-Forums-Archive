---
title: "USB HDD not recognized"
date: 2014-05-04
forum: Hardware
---

### Post by cscj01 on 2014-05-04
I have a Seagate HDD that I have been using for system backups/restores with Clonezilla.  It has always worked.  I started a backup today.  During the backup, we had a power glitch.  Now the system nor Clonezilla and Gparted Live CDs will recognize the drive.  However, the system powers the drive up, but lsusb does not list it.  My assumption is the disk has no partition on it (or at least no clean partition on it), and therefore it is not showing up.  Is there any way I can format this HDD with a live cd or special software of which I am not aware?  I am runnung Ubuntu 12.04.4 with Gnome Classic (or Fallback or Whatever it's called now) DE.

---

### Post by Bashing-om on 2014-05-04
cscj01; Hi !

With the external disk connected, power up and boot up -> does bios see the hard drive ?
What format is used on that external drive ? EXT4, NTFS, other ?

Does the tool 'fdisk' see that external drive "
```

sudo fdisk -lu

```

Else, may see what the utility 'testdisk' can do.
```

sudo apt-get install testdisk

```
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://ubuntuforums.org/showthread.php?t=2112112](http://ubuntuforums.org/showthread.php?t=2112112) <- Cheesemill post #7

Spare off the superblock ??
Maybe:
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

There are those times a loss of power is real bad. But ->

[INDENT][INDENT]where there is life
[INDENT][INDENT][INDENT]there is hope
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cscj01 on 2014-05-04
I tried lsusb -v and this showed up in the list```
Bus 001 Device 009: ID 0bc2:3001 Seagate RSS LLC 
Device Descriptor:
  bLength                18
  bDescriptorType         1Bus 001 Device 009: ID 0bc2:3001 Seagate RSS LLC Bus 001 Device 009: ID 0bc2:3001 Seagate RSS LLC 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bc2 Seagate RSS LLC
  idProduct          0x3001 
  bcdDevice            0.00
  iManufacturer           1 Seagate
  iProduct                2 FreeAgent
  iSerial                 3 2GEVDW9L
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          5 Config0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              4 Interface0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bc2 Seagate RSS LLC
  idProduct          0x3001 
  bcdDevice            0.00
  iManufacturer           1 Seagate
  iProduct                2 FreeAgent
  iSerial                 3 2GEVDW9L
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          5 Config0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              4 Interface0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bc2 Seagate RSS LLC
  idProduct          0x3001 
  bcdDevice            0.00
  iManufacturer           1 Seagate
  iProduct                2 FreeAgent
  iSerial                 3 2GEVDW9L
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          5 Config0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              4 Interface0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```Also, fdisk -lu did not show the disk.

I installed testdisk and ran it, and it did show the HDD, but it was not able to correct any disk issues.  I first did an Analyze and had many read areas.  Then I tried to recover a partition, but to no avail.  I could not write a new MBR or clear the partition table.  So I think I need some tool to format the HDD.

---

### Post by Bashing-om on 2014-05-05
cscj01; Umph;

Sorry, if GParted and/or testdisk can not handle the job, I am sorta grasping here.
Might try and download and burn the testdisk CD, and see what "photorec" can do for you.

[INDENT]this too would be
[INDENT][INDENT][INDENT]a learning experience for me
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cscj01 on 2014-05-09
Well, I decided if I would use dd to write zeros to the drive.  Although it took 4 1/2 days, it completed successfully.  However, I still get I/O errors if I attempt to create a partition table.  That doesn't seem right to me.  If dd can write to all of the drive, why can I not create a partition table on it.  Perhaps there is something about dd that I do not understand.

BTW, every application sees the drive now; Disk Utils, Gparted, parted, Testdisk.  However none can do anything with it.  I'm going to try to use it as the target in a Clonezilla operation again.  Perhaps Clonezilla can work with it.  I hope I do not get a power glitch during this attempt.

---

### Post by Bashing-om on 2014-05-09
cscj01; Humm,

I have had good results reclaiming hard drives with 'dd' !
```

sudo dd if=/dev/zero of=/dev/sda bs=1M

```
That the code you ran ?
By the way you can get a status of dd, see the man page for the procedure.
```

man dd

```
In my experience with the arguments given, should take an hour per gig.
I format and partition from terminal:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

And I am set to go.

[INDENT][INDENT]hope your results are similar
[/INDENT][/INDENT]

---

