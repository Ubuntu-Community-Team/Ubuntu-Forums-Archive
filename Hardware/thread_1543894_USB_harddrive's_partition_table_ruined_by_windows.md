---
title: "USB harddrive's partition table ruined by windows"
date: 2010-08-01
forum: Hardware
---

### Post by miloE on 2010-08-01
Hello folks

I was backing up data from my work pc that uses win XP, to my 500GB usb hdd.  But the damn windows somehow corrupted it.

Now...came home to put it into another pc with Ubuntu...same thing, drive not automatically recognized.  BUT, Gparted does see the drive.

Also, when I plug it in and then check syslog. indeed Ubuntu tries to mount it

```

Aug  1 14:49:46 eeEmilux kernel: [ 8027.585091] usb 5-1: new high speed USB device using ehci_hcd and address 5
Aug  1 14:49:46 eeEmilux kernel: [ 8027.734073] usb 5-1: configuration #1 chosen from 1 choice
Aug  1 14:49:46 eeEmilux kernel: [ 8027.744377] scsi7 : SCSI emulation for USB Mass Storage devices
Aug  1 14:49:46 eeEmilux kernel: [ 8027.764414] usb-storage: device found at 5
Aug  1 14:49:46 eeEmilux kernel: [ 8027.764425] usb-storage: waiting for device to settle before scanning
Aug  1 14:49:51 eeEmilux kernel: [ 8032.764341] usb-storage: device scan complete
Aug  1 14:49:51 eeEmilux kernel: [ 8032.764902] scsi 7:0:0:0: Direct-Access     ST350082 0AS                   PQ: 0 ANSI: 2 CCS
Aug  1 14:49:51 eeEmilux kernel: [ 8032.769894] sd 7:0:0:0: [sdc] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Aug  1 14:49:51 eeEmilux kernel: [ 8032.771271] sd 7:0:0:0: [sdc] Write Protect is off
Aug  1 14:49:51 eeEmilux kernel: [ 8032.771286] sd 7:0:0:0: [sdc] Mode Sense: 34 00 00 00
Aug  1 14:49:51 eeEmilux kernel: [ 8032.771294] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Aug  1 14:49:51 eeEmilux kernel: [ 8032.772551] sd 7:0:0:0: [sdc] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Aug  1 14:49:51 eeEmilux kernel: [ 8032.796979] sd 7:0:0:0: [sdc] Write Protect is off
Aug  1 14:49:51 eeEmilux kernel: [ 8032.796997] sd 7:0:0:0: [sdc] Mode Sense: 34 00 00 00
Aug  1 14:49:51 eeEmilux kernel: [ 8032.797061] sd 7:0:0:0: [sdc] Assuming drive cache: write through
**[COLOR=Red]Aug  1 14:49:51 eeEmilux kernel: [ 8032.799474]  sdc: unknown partition table[/COLOR]**

```Sooo...no partition table.  windows corrupted it!


this is what lsusb says

```
milux@eeEmilux:~$ lsusb -v

Bus 005 Device 005: ID 059b:0370 Iomega Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x059b Iomega Corp.
  idProduct          0x0370 
  bcdDevice            0.00
  iManufacturer          10 Iomega
  iProduct               11 External HD
  iSerial                 5 927FFFFFFFFF
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 USB Mass Storage
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
      iInterface              6 MSC Bulk-Only Transfer
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
can't get debug descriptor: Connection timed out
Device Status:     0x0001
  Self Powered

```

By looking for information on this nice forum, i saw some commands that could help:  testdisk, photorec, fsck, ddrescue

I gave it a shot at testdisk...the actual name i originally gave to my hdd was seen!  But I down want to ruin the data, I got to a point where this is seen

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdc - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
[COLOR=DarkGreen][COLOR=Red]*[/COLOR] HPFS - NTFS              0   1  1 60800 254 63  976768002 [Discototote_Iomega_HDD]
[/COLOR]

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 500 GB / 465 GiB

```When I press left or right, i get these options *  , D  , P .

Which one should I choose?

From your point of view, should I use some other method to recover the partition table?

Thanks in advance

---

### Post by Sef on 2010-08-01
I would suggest [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to recovery your data and partition.

---

### Post by efflandt on 2010-08-02
I would think that you would want to pick **P** to make it a primary partition.  D would delete it and it does not need to be bootable if it is just data.  It looks like it would end up the proper size for a single partition on 500 GB drive.

Note that just altering the partition table does not delete any data.  If it is readable then, you may want to run **chkdsk /f** on it from Windows to make sure there are no errors from something being incompletely written to it.

---

