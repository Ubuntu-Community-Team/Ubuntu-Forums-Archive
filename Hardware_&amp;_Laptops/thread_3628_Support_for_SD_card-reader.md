---
title: "Support for SD card-reader?"
date: 2004-11-08
forum: Hardware &amp; Laptops
---

### Post by zerohalo on 2004-11-08
I have a Compaq Presario X1000 (which is, hardware-wise, the same model as the HP zt3000 and the nx7000). It comes with a built-in SD card-reader (which is becoming more popular in new laptop models these days). Ubuntu doesn't seem to support it from what I can tell--Gnome-HAL doesn't detect it. Is there any chance of getting drivers for Ubuntu that will make it work?

Does anyone else have the same problem and if so, have you found a workaround?

Ubuntu seems like a great release--detected the rest of the hardware on my laptop ok--just not the SD card reader. 

Thanks!

---

### Post by louisamaus on 2004-11-20
I have the problem with my usb card-reader.
How can i mount it. Ubuntu does not see it.

May it can help, take a look at this:

root@ubuntu:/home/christoph # cat /proc/scsi/scsi
Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: SMSC     Model: 223 U HS-CF      Rev: 1.95
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 01
  Vendor: SMSC     Model: 223 U HS-MS      Rev: 1.95
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 02
  Vendor: SMSC     Model: 223 U HS-SM      Rev: 1.95
  Type:   Direct-Access                    ANSI SCSI revision: 02
[COLOR=DarkRed]Host: scsi1 Channel: 00 Id: 00 Lun: 03
  Vendor: SMSC     Model: 223 U HS-SD/MMC  Rev: 1.95
  Type:   Direct-Access                    ANSI SCSI revision: 02

[/COLOR]

---

### Post by randy on 2004-11-20
Is it listed in the output of lshal or lspci?

---

### Post by louisamaus on 2004-11-20
root@ubuntu:/home/christoph # lshal
udi = '/org/freedesktop/Hal/devices/block_8_48'
  volume.is_partition = false  (bool)
  info.udi = '/org/freedesktop/Hal/devices/block_8_48'  (string)
  storage.hotpluggable = true  (bool)
  storage.removable = true  (bool)
  info.product = [COLOR=DarkRed]'223 U HS-SD/MMC'  (string)[/COLOR] * Is it here ?*
  info.vendor = 'SMSC'  (string)
  storage.drive_type = 'disk'  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/block_8_48'  (string)
  storage.physical_device = '/org/freedesktop/Hal/devices/usb_usb_device_424_223 a_195_-1_031017200000_0'  (string)
  storage.vendor = 'SMSC'  (string)
  storage.model = '223 U HS-SD/MMC'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.no_partitions_hint = false  (bool)
  storage.media_check_enabled = true  (bool)
  storage.bus = 'usb'  (string)
  block.minor = 48  (0x30)  (int)
  block.major = 8  (0x8)  (int)
  info.capabilities = 'block storage'  (string)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/scsi_1_0_0_3'  (string)
  block.device = '/dev/sdd'  (string)
  block.is_volume = false  (bool)
  block.have_scanned = true  (bool)
  block.no_partitions = false  (bool)
  linux.sysfs_path_device = '/sys/block/sdd'  (string)
  linux.sysfs_path = '/sys/block/sdd'  (string)
  info.bus = 'block'  (string)

*************************************************************************
root@ubuntu:/home/christoph # lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro13 3x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev  21)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 0d)
0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
0000:00:11.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Ra deon 7000/VE]
0000:00:12.0 USB Controller: NEC Corporation USB (rev 41)
0000:00:12.1 USB Controller: NEC Corporation USB (rev 41)
0000:00:12.2 USB Controller: NEC Corporation USB 2.0 (rev 01)
0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:00:14.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10 )
root@ubuntu:/home/christoph #
_____________________________________________________________________

---

### Post by randy on 2004-11-20
It's definitely being picked up by hal as a device.  When you insert a card what is the output of dmesg?

---

### Post by louisamaus on 2004-11-21
root@ubuntu:/home/christoph # dmesg
.....

Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
  Vendor: SMSC      Model: 223 U HS-MS       Rev: 1.95
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdb at scsi1, channel 0, id 0, lun 1
  Vendor: SMSC      Model: 223 U HS-SM       Rev: 1.95
  Type:   Direct-Access                      ANSI SCSI revision: 02
[COLOR=DarkRed]Attached scsi removable disk sdc at scsi1, channel 0, id 0, lun 2
  Vendor: SMSC      Model: 223 U HS-SD/MMC   Rev: 1.95[/COLOR]
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sdd: 512000 512-byte hdwr sectors (262 MB)
sdd: Write Protect is off

---

### Post by randy on 2004-11-21
You should be available as /dev/sdc.  The partition is probably /dev/scd1

---

### Post by zerohalo on 2004-11-22
louisamaus, do you have a built-in SD card reader, or an external one? 

I have the built-in one, and HAL doesn't detect it at all. cat /proc/scsi/scsi returns nothing, and lshal doesn't provide any info related to an SD card reader from what I can tell :-(. dmesg gives no output when I insert the card.

---

### Post by louisamaus on 2004-11-23
I have an external USB Card-Reader

Yeahh, it's there, but ... !!

I ca see my card-reader with:  
root@ubuntu:/media/windows/mmc # fdisk -l

Disk /dev/hda: 1282 MB, 1282498560 bytes
64 heads, 63 sectors/track, 621 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         621     1249920    6  FAT16

Disk /dev/hdb: 10.2 GB, 10245537792 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1          13      104391   83  Linux
/dev/hdb2   *          14         663     5221125   83  Linux
/dev/hdb3             664        1245     4674915    5  Extended
/dev/hdb5             697        1245     4409811    7  HPFS/NTFS
/dev/hdb6             664         696      265009+  82  Linux swap

Partition table entries are not in disk order

Disk /dev/sdd: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1001      256000    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1000, 15, 32) logical=(1000, 0, 32)

I make these steps:
1. mkdir /media/windows/mmc
2. mount -t  vfat /dev/sdd1 /media/windows/mmc

So now i can read and write my mmc-card, but it has only 46,3 mb free space.
What's wrong, the mmc-card has  256 mb free ?

---

### Post by kreawit on 2004-11-26
I think this tread went out of line.

I'm also interested in mounting my BUILT IN SD-card reader bundled with my HP nx7000.

There is no sign of any /dev/sdXX

For now I do can mount externa SD-readers using USB, but using the built-in reader would still be nice.

/Anders

---

