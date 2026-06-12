---
title: "USB DVD-ROM not being mounted"
date: 2024-01-30
forum: Hardware
---

### Post by silvergreen93 on 2024-01-30
Hi all,

I am using a brand new Raspberry Pi 5 with official Ubuntu 23.10 and want to connect a USB 3.0 to SATA adapter with an external DVD-RW drive.
Unfortunately, plugging it in does not do anything. Also trying to mount it from /dev I cannot find any dvd-rom/cd-rom there.
Here are some outputs from the debugging commands that I tried while investigating the issue:

```

mihai@rpi5:/dev$ dmesg
[  641.453646] usb 3-1: new high-speed USB device number 3 using xhci-hcd
[  641.602208] usb 3-1: New USB device found, idVendor=13fd, idProduct=0840, bcdDevice= 1.14
[  641.602217] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  641.602221] usb 3-1: Product: External
[  641.602224] usb 3-1: Manufacturer: Generic
[  641.602227] usb 3-1: SerialNumber: 303130313830323832383432
[  641.602786] usb-storage 3-1:1.0: USB Mass Storage device detected
[  641.602995] scsi host0: usb-storage 3-1:1.0
[  642.627416] scsi 0:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A5SH XD13 PQ: 0 ANSI: 0
[  642.627709] scsi 0:0:0:0: Attached scsi generic sg0 type 5

```

```

mihai@rpi5:/dev$ cdrecord -scanbus
scsibus0:
        0,0,0     0) 'PLDS    ' 'DVD+-RW DS-8A5SH' 'XD13' Removable CD-ROM

```

```

mihai@rpi5:/dev$ sudo lshw -C disk
  *-cdrom UNCLAIMED
       description: SCSI CD-ROM
       product: DVD+-RW DS-8A5SH
       vendor: PLDS
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       version: XD13
       capabilities: removable

```

```

mihai@rpi5:/dev$ lsusb -v
Bus 003 Device 003: ID 13fd:0840 Initio Corporation INIC-1618L SATA
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x13fd Initio Corporation
  idProduct          0x0840 INIC-1618L SATA
  bcdDevice            1.14
  iManufacturer           1 Generic
  iProduct                2 External
  iSerial                 3 303130313830323832383432
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0020
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
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
      bInterfaceSubClass      2 SFF-8020i, MMC-2 (ATAPI)
      bInterfaceProtocol     80
      iInterface              0
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

```


Can you suggest what might be wrong? I think there is no driver for this loaded in the kernel. If so, what can I do to make it work?

Thanks!

---

### Post by MAFoElffen on 2024-01-30
Please post the output of this within CODE Tags
```

wodim --checkdrive
wodim -scanbus
wodim --devices

```
And is this drive connected to an externally powered hub, so if it needs more power to work... Just thinking.

---

### Post by silvergreen93 on 2024-01-31
Here are the outputs:

```

mihai@rpi5:~$ wodim --checkdrive
Device was not specified. Trying to find an appropriate drive...
Using drive: /dev/sg0
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'PLDS    '
Identification : 'DVD+-RW DS-8A5SH'
Revision       : 'XD13'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

```

```

mihai@rpi5:~$ wodim --scanbus
scsibus0:
        0,0,0     0) 'PLDS    ' 'DVD+-RW DS-8A5SH' 'XD13' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *

```

```

mihai@rpi5:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg0'      rwrw-- : 'PLDS' 'DVD+-RW DS-8A5SH'
-------------------------------------------------------------------------

```

Also, when I try to mount the indicated device I get:

```

mihai@rpi5:/mnt$ sudo mount /dev/sg0 /mnt/cdrom
mount: /mnt/cdrom: /dev/sg0 is not a block device.
       dmesg(1) may have more information after failed mount system call.

```

The DVD-RW works fine on all other devices (Windows PC, laptop) directly connected to USB3.0 port, no power source needed.

---

### Post by TheFu on 2024-01-31
Specify the type of file system.  For data, that is usually iso9660 or udf.  For music, I don't know the type.  Try this:
```
sudo mount -t iso9660  /dev/sg0 /mnt/cdrom
```
or 
```
sudo mount -t udf  /dev/sg0 /mnt/cdrom
```

I have a USB DVD reader ... let me turn on my Pi4 and see if it works for a data DVD.  **dmesg** sees this:
```
[   74.718742] Buffer I/O error on dev sr0, logical block 1413248, async page read
[   74.929015] sr 0:0:0:0: [sr0] tag#0 UNKNOWN(0x2003) Result: hostbyte=0x00 driverbyte=DRIVER_OK cmd_age=0s
[   74.929034] sr 0:0:0:0: [sr0] tag#0 Sense Key : 0x5 [current] 
[   74.929041] sr 0:0:0:0: [sr0] tag#0 ASC=0x6f ASCQ=0x3 
[   74.929050] sr 0:0:0:0: [sr0] tag#0 CDB: opcode=0x28 28 00 00 00 04 00 00 00 02 00 00 00
[   74.929057] blk_update_request: I/O error, dev sr0, sector 4096 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 0
[   74.992218] sr 0:0:0:0: [sr0] tag#0 UNKNOWN(0x2003) Result: hostbyte=0x00 driverbyte=DRIVER_OK cmd_age=0s
[   74.992247] sr 0:0:0:0: [sr0] tag#0 Sense Key : 0x5 [current] 
[   74.992257] sr 0:0:0:0: [sr0] tag#0 ASC=0x6f ASCQ=0x3 
[   74.992268] sr 0:0:0:0: [sr0] tag#0 CDB: opcode=0x28 28 00 00 00 04 00 00 00 02 00 00 00
[   74.992277] blk_update_request: I/O error, dev sr0, sector 4096 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[   74.992293] Buffer I/O error on dev sr0, logical block 512, async page read
[   75.453649] UDF-fs: INFO Mounting volume 'FULL_METAL_JACKET_4X3PS_NA', timestamp 1999/04/21 02:14 (1000)
```

So, it was mounted automatically, 
```
/media/FULL_METAL_JACKET_4X3PS_NA/VIDEO_TS$ ll
total 5652922
-r--r--r-- 1 osmc osmc       8192 Apr 20  1999 VIDEO_TS.BUP
-r--r--r-- 1 osmc osmc       8192 Apr 20  1999 VIDEO_TS.IFO
-r--r--r-- 1 osmc osmc      83968 Apr 20  1999 VTS_01_0.BUP
-r--r--r-- 1 osmc osmc      83968 Apr 20  1999 VTS_01_0.IFO
-r--r--r-- 1 osmc osmc    2002944 Apr 20  1999 VTS_01_0.VOB
-r--r--r-- 1 osmc osmc 1073739776 Apr 20  1999 VTS_01_1.VOB
-r--r--r-- 1 osmc osmc 1073739776 Apr 20  1999 VTS_01_2.VOB
-r--r--r-- 1 osmc osmc 1073739776 Apr 20  1999 VTS_01_3.VOB
-r--r--r-- 1 osmc osmc  742830080 Apr 20  1999 VTS_01_4.VOB
-r--r--r-- 1 osmc osmc 1073739776 Apr 20  1999 VTS_01_5.VOB
-r--r--r-- 1 osmc osmc  748615680 Apr 20  1999 VTS_01_6.VOB
```

This DVD device doesn't have external power.  Also, it doesn't run Ubuntu. Is it running Debian.
```
$ lsb_release -d
Description:    Debian GNU/Linux 11 (bullseye)
```

It "just worked". Sorry. That probably isn't too much help.  I do specifically purchase hardware that is known to "just work" with Linux.  Also, 
```
$ uname -a
Linux pi4 5.15.92-1-osmc #1 SMP PREEMPT Tue Jul 25 00:03:42 UTC 2023 aarch64 GNU/Linux
```

For the kernel version used.
The device is:
```
$ ll /dev/sr0 
brw-rw---- 1 root cdrom 11, 0 Jan 31 11:01 /dev/sr0

```

---

### Post by MAFoElffen on 2024-02-01
> **silvergreen93 said:**
> 
```

mihai@rpi5:/mnt$ sudo mount /dev/sg0 /mnt/cdrom
mount: /mnt/cdrom: /dev/sg0 is not a block device.
       dmesg(1) may have more information after failed mount system call.

```

The DVD-RW works fine on all other devices (Windows PC, laptop) directly connected to USB3.0 port, no power source needed.
???

That is not how that works. sg devices are just a basic generic SCSI layer. You cannot mount to that generic layer. /dev/sg0 is mapped to some other device name. Usually if an optical drive, it is mapped to an /dev/srX device name.

If you install package 'sg3-utils' (not installed by default), then you can use the 'sg_map' command to see what the sg devices are mapped to, then you use that device name to mount that.
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ sudo sg_map
/dev/sg0  /dev/sda
/dev/sg1  /dev/sdb
/dev/sg2  /dev/sdc

```
Does that make more sense now why that failed?

But since it is coming up as SCSI, use 
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ lsscsi -l
[0:0:0:0]    disk    ATA      Samsung SSD 870  2B6Q  /dev/sda 
  state=running queue_depth=32 scsi_level=6 type=0 device_blocked=0 timeout=30
[1:0:0:0]    disk    ATA      Samsung SSD 870  2B6Q  /dev/sdb 
  state=running queue_depth=32 scsi_level=6 type=0 device_blocked=0 timeout=30
[2:0:0:0]    disk    ATA      Dogfish SSD 2TB  1A0   /dev/sdc 
  state=running queue_depth=32 scsi_level=6 type=0 device_blocked=0 timeout=30

```

---

### Post by silvergreen93 on 2024-02-03
> **MAFoElffen said:**
> 

If you install package 'sg3-utils' (not installed by default), then you can use the 'sg_map' command to see what the sg devices are mapped to, then you use that device name to mount that.



Thanks, here is the output from sg_map:

```
mihai@rpi5:~$ sudo sg_map
/dev/sg0

```
And here is from lsscsi:


```
mihai@rpi5:~$ lsscsi -l
[0:0:0:0]    cd/dvd  PLDS     DVD+-RW DS-8A5SH XD13  -
  state=running queue_depth=1 scsi_level=0 type=5 device_blocked=0 timeout=30

```

I can see that there is no /dev/sda or any other mapping.

---

### Post by silvergreen93 on 2024-02-12
Anything I can do to make [COLOR=#000000][FONT=&quot]sg_map map it properly?[/FONT][/COLOR]

---

### Post by TheFu on 2024-02-12
> **silvergreen93 said:**
> Anything I can do to make [COLOR=#000000][FONT=&quot]sg_map map it properly?[/FONT][/COLOR]

I'm a person that needs things to work, even if I'm not "correct".  There's a point where spending time on a $25 problem just isn't worth it.  The USB3 DVD±RW drive I used above is Amicool [https://www.amazon.com/External-Amicool-Portable-Rewriter-Duplicator/dp/B07V67STBD](https://www.amazon.com/External-Amicool-Portable-Rewriter-Duplicator/dp/B07V67STBD)  The listing title says that it works with Linux - and it does.  I've used it with x86-64 and aarch64 Linux. Plug it in. It works.

The question is, "how bad do you want to be right?"   I just want things to work as expected.  Sometimes that means swapping hardware and moving on.

---

### Post by #&amp;thj^% on 2024-02-12
I'm also one That just needs things to work as expected.
Some hardware might need a gentle poke:
```
sudo modprobe sg

```

---

### Post by silvergreen93 on 2024-02-14
> **TheFu said:**
> I'm a person that needs things to work, even if I'm not "correct".  There's a point where spending time on a $25 problem just isn't worth it.  The USB3 DVD±RW drive I used above is Amicool [https://www.amazon.com/External-Amicool-Portable-Rewriter-Duplicator/dp/B07V67STBD](https://www.amazon.com/External-Amicool-Portable-Rewriter-Duplicator/dp/B07V67STBD)  The listing title says that it works with Linux - and it does.  I've used it with x86-64 and aarch64 Linux. Plug it in. It works.

The question is, "how bad do you want to be right?"   I just want things to work as expected.  Sometimes that means swapping hardware and moving on.

I too like things to work without tinkering around, but in this case I will also not learn anything about Linux if I just discard the current hardware to replace it with one that might or might not work (I have no guarantee that that drive will work on my OS-arch combination).

Here I am trying to find out why it doesn't work and what it needs to be properly working. I reached a point where I think I am close to the actual issue.

---

### Post by TheFu on 2024-02-14
> **silvergreen93 said:**
> I too like things to work without tinkering around, but in this case I will also not learn anything about Linux if I just discard the current hardware to replace it with one that might or might not work (I have no guarantee that that drive will work on my OS-arch combination).

Here I am trying to find out why it doesn't work and what it needs to be properly working. I reached a point where I think I am close to the actual issue.

I tested it on a pi4 running a debian-based distro. Don't know how much more you expect it to be "like".  Hardware being non-supported can eat lots of time and always be "close to working", but never actually work.

I hope you find a solution, but it has been 2 weeks already.

---

### Post by silvergreen93 on 2024-04-30
I am happy to report that today I installed Ubuntu 24.04 LTS and the DVD-ROM is now working! Seems that the new kernel has the driver built-in.
See dmesg logs:

```
[   66.269326] usb 4-1: new high-speed USB device number 3 using xhci-hcd
[   66.395889] usb 4-1: New USB device found, idVendor=13fd, idProduct=0840, bcdDevice= 1.14
[   66.395898] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   66.395903] usb 4-1: Product: External
[   66.395906] usb 4-1: Manufacturer: Generic
[   66.395909] usb 4-1: SerialNumber: 303130313830323832383432
[   67.628683] usb-storage 4-1:1.0: USB Mass Storage device detected
[   67.628938] scsi host0: usb-storage 4-1:1.0
[   67.629130] usbcore: registered new interface driver usb-storage
[   68.645219] scsi 0:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A5SH XD13 PQ: 0 ANSI: 0
[   68.645576] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   68.665452] sr 0:0:0:0: Power-on or device reset occurred
[   68.670638] sr 0:0:0:0: [sr0] scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[   68.670648] cdrom: Uniform CD-ROM driver Revision: 3.20
[   68.673126] sr 0:0:0:0: Attached scsi CD-ROM sr0

```

---

