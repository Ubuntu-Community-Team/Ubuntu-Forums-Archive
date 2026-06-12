---
title: "External Hard drive not mounting"
date: 2010-04-13
forum: Hardware
---

### Post by benbeel on 2010-04-13
I have a seagate 320 gb external hard drive in a Rosewill RX35 enclosure (board in the enclosure is by prolific technologies, inc.) This is a self-powered enclosure, IDE to USB hookup to the computer, and the hard drive is freshly formatted to ext3. I am running Ubuntu 9.04 on my laptop, a dell vostro 1000. When I plug the hard drive into the usb port, it does not get mounted. It does not show up in /media either. 

> lsusb output:
Bus 001 Device 002: ID 067b:2506 Prolific Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Device 002 is the external hard drive.

> fdisk -l output:
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

/dev/sda is my internal (master) hard drive in the laptop.

lspci does not show the hard drive on any of the USB ports.

Interestingly, in the syslog I get the following after plugging in the hard drive:
> Apr 13 14:50:27 ben-laptop kernel: [ 2284.941514] sd 6:0:0:0: Attached scsi generic sg2 type 0
Apr 13 14:50:31 ben-laptop kernel: [ 2288.552047] usb 1-3: new high speed USB device using ehci_hcd and address 3
Apr 13 14:50:31 ben-laptop kernel: [ 2288.728715] usb 1-3: configuration #1 chosen from 1 choice
Apr 13 14:50:31 ben-laptop kernel: [ 2288.773323] scsi7 : SCSI emulation for USB Mass Storage devices
Apr 13 14:50:31 ben-laptop kernel: [ 2288.776678] usb-storage: device found at 3
Apr 13 14:50:31 ben-laptop kernel: [ 2288.776685] usb-storage: waiting for device to settle before scanning
Apr 13 14:50:36 ben-laptop kernel: [ 2293.776322] usb-storage: device scan complete
Apr 13 14:50:36 ben-laptop kernel: [ 2293.811701] scsi 7:0:0:0: Direct-Access     ST332062 0AV              3.AC PQ: 0 ANSI: 0
Apr 13 14:50:36 ben-laptop kernel: [ 2293.815638] sd 7:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 13 14:50:36 ben-laptop kernel: [ 2293.865672] sd 7:0:0:0: [sdb] Write Protect is off
Apr 13 14:50:36 ben-laptop kernel: [ 2293.865682] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
Apr 13 14:50:36 ben-laptop kernel: [ 2293.865689] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Apr 13 14:50:36 ben-laptop kernel: [ 2293.867022] sd 7:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 13 14:50:36 ben-laptop kernel: [ 2293.869533] sd 7:0:0:0: [sdb] Write Protect is off
Apr 13 14:50:36 ben-laptop kernel: [ 2293.869541] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
Apr 13 14:50:36 ben-laptop kernel: [ 2293.869547] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Apr 13 14:51:07 ben-laptop kernel: [ 2293.869562]  sdb:<6>usb 1-3: reset high speed USB device using ehci_hcd and address 3
Apr 13 14:51:38 ben-laptop kernel: [ 2355.112062] usb 1-3: reset high speed USB device using ehci_hcd and address 3
Apr 13 14:52:09 ben-laptop kernel: [ 2386.112062] usb 1-3: reset high speed USB device using ehci_hcd and address 3
Apr 13 14:52:40 ben-laptop kernel: [ 2417.112556] usb 1-3: reset high speed USB device using ehci_hcd and address 3
Apr 13 14:53:42 ben-laptop kernel: [ 2479.112070] usb 1-3: reset high speed USB device using ehci_hcd and address 3
Apr 13 14:53:42 ben-laptop kernel: [ 2479.245414] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Apr 13 14:53:42 ben-laptop kernel: [ 2479.245421] end_request: I/O error, dev sdb, sector 0
Apr 13 14:53:42 ben-laptop kernel: [ 2479.245427] Buffer I/O error on device sdb, logical block 0
Apr 13 14:54:13 ben-laptop kernel: [ 2510.112235] usb 1-3: reset high speed USB device using ehci_hcd and address 3

The reset is then just repeated over and over again in the syslog. I have tried plugging the hard drive into every USB port on the machine, with similar results. I tried plugging the hard drive into an EEE PC running UNR 9.10, with the exact same results. USB sticks and a self-powered USB hard drive have worked and still work fine: recognized and mounted automatically. I would like to get this big ol' external up and running, and am praying that there is a solution better than "get a different enclosure." Does anyone know what's going on here? I can provide more info if needed. THANK YOU!!!

---

### Post by paris_l87 on 2010-04-15
i have the same issue using ubuntu 10.04beta2 
i could mount my hd normally on 9.10 and i can still mount it on windows XP.i guess it has sth to do with the new distribution.
my dmesg:

> [ 2331.420177] usb 1-4: new high speed USB device using ehci_hcd and address 19
[ 2331.562933] usb 1-4: configuration #1 chosen from 1 choice
[ 2331.594080] scsi13 : SCSI emulation for USB Mass Storage devices
[ 2331.594432] usb-storage: device found at 19
[ 2331.594439] usb-storage: waiting for device to settle before scanning
[ 2336.592431] usb-storage: device scan complete
[ 2336.595082] scsi 13:0:0:0: Direct-Access     Apacer    Technology Inc. 0009 PQ: 0 ANSI: 0
[ 2336.601652] sd 13:0:0:0: Attached scsi generic sg2 type 0
[ 2336.610147] sd 13:0:0:0: [sdb] 976773164 512-byte logical blocks: (500 GB/465 GiB)
[ 2336.611078] sd 13:0:0:0: [sdb] Write Protect is off
[ 2336.611082] sd 13:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2336.611086] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 2336.614088] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 2336.614096]  sdb: sdb1
[ 2336.685943] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 2336.685956] sd 13:0:0:0: [sdb] Attached SCSI disk
[ 2344.112136] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2352.112159] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2383.112077] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2414.100123] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2445.100257] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2476.101069] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2507.100061] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2538.100154] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2538.236416] sd 13:0:0:0: [sdb] Unhandled error code
[ 2538.236426] sd 13:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 2538.236436] sd 13:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[ 2538.236463] end_request: I/O error, dev sdb, sector 63
[ 2538.236476] Buffer I/O error on device sdb1, logical block 0
[ 2538.236487] Buffer I/O error on device sdb1, logical block 1
[ 2538.236494] Buffer I/O error on device sdb1, logical block 2
[ 2538.236502] Buffer I/O error on device sdb1, logical block 3
[ 2569.112085] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2600.100190] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2631.100093] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2662.100080] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2693.100581] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2724.100130] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2724.236338] sd 13:0:0:0: [sdb] Unhandled error code
[ 2724.236348] sd 13:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 2724.236359] sd 13:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 02 00
[ 2724.236385] end_request: I/O error, dev sdb, sector 63
[ 2724.236399] Buffer I/O error on device sdb1, logical block 0
[ 2755.100141] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2786.100276] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2817.100160] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2848.112090] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2879.112142] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2910.113135] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2910.248166] sd 13:0:0:0: [sdb] Unhandled error code
[ 2910.248177] sd 13:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 2910.248187] sd 13:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 41 00 00 02 00
[ 2910.248214] end_request: I/O error, dev sdb, sector 65
[ 2910.248227] Buffer I/O error on device sdb1, logical block 1
[ 2941.112049] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 2972.112143] usb 1-4: reset high speed USB device using ehci_hcd and address 19
[ 3003.112118] usb 1-4: reset high speed USB device using ehci_hcd and address 19

can anyone help?

---

### Post by trooperchix on 2010-04-15
I have the same issue and I am running karmic and using a Western Digital 500 Gb drive, brand new, straight from the box.  Not being recognized at all.  Help!!

---

### Post by paris_l87 on 2010-04-16
well seems it was a kernel issue,after the update and the new kernel it works! :)
:guitar::guitar:

---

### Post by FenwayFrank on 2010-04-24
No such luck here:
Host machine is a Sony VAIO VGN-FZ340E; drive is a 40 GB Maxtor 3000LS
I've tried swapping USB connectors, power bricks, etc; nothing.

Any other suggestions as to what I can peruse, poke or prod would be appreciated.
~~
```
root@frank-laptop:/mnt/ubuntu_9.04/home/frank# uname -a

Linux frank-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux


root@frank-laptop:/mnt/ubuntu_9.04/home/frank# tail /var/log/messages

Apr 24 13:14:16 frank-laptop kernel: [  159.820099] usb 2-2: new high speed USB device using ehci_hcd and address 4
Apr 24 13:14:16 frank-laptop kernel: [  159.971122] usb 2-2: configuration #1 chosen from 1 choice
Apr 24 13:14:16 frank-laptop kernel: [  159.984584] scsi6 : SCSI emulation for USB Mass Storage devices
Apr 24 13:14:42 frank-laptop kernel: [  186.130109] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Apr 24 13:14:52 frank-laptop kernel: [  196.400131] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Apr 24 13:14:57 frank-laptop kernel: [  201.672611] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Apr 24 13:15:08 frank-laptop kernel: [  211.950116] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Apr 24 13:15:08 frank-laptop kernel: [  212.103162] scsi 6:0:0:0: Device offlined - not ready after error recovery


root@frank-laptop:/mnt/ubuntu_9.04/home/frank# lsusb -s2:4

Bus 002 Device 004: ID 0d49:3005 Maxtor 


root@frank-laptop:/mnt/ubuntu_9.04/home/frank# lsusb -s2:4 -v

Bus 002 Device 004: ID 0d49:3005 Maxtor 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0d49 Maxtor
  idProduct          0x3005 
  bcdDevice            1.00
  iManufacturer          56 Maxtor
  iProduct               63 3000LS v01.00.00
  iSerial                80 DEF10651D73C
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
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
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
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
  Self Powered[/FONT]
```

---

### Post by P-Hell on 2010-04-24
Hi, I have a similar problem. My hard drive is a Lacie 2big external RAID drive. It's working perfectly on Windows, on Kubuntu 8.04 and on Ubuntu/Kubuntu 10.04 RC live CDs.

But when I install Kubuntu 10.04 RC, the hard drive is not mountable. It'S partition appears when I use the *fdisk* command:
```
Disque /dev/sdf: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x454c4d03

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS
```(sorry for the french quote)

It also appears when I use the *lsusb* command:
```
Bus 001 Device 006: ID 059f:1009 LaCie, Ltd
```But is I try to list the hard drives in */dev*, it appears as a disk but not as a partition (*sdf* is the drive I'm talking about):
```
pierre-luc@Andrea:~$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2010-04-24 13:43 /dev/sda
brw-rw---- 1 root disk 8,  1 2010-04-24 13:43 /dev/sda1
brw-rw---- 1 root disk 8,  2 2010-04-24 13:43 /dev/sda2
brw-rw---- 1 root disk 8, 16 2010-04-24 13:43 /dev/sdb
brw-rw---- 1 root disk 8, 32 2010-04-24 13:43 /dev/sdc
brw-rw---- 1 root disk 8, 48 2010-04-24 13:43 /dev/sdd
brw-rw---- 1 root disk 8, 64 2010-04-24 13:43 /dev/sde
brw-rw---- 1 root disk 8, 80 2010-04-24 14:24 /dev/sdf

```I tried with another external hard drive (a simple drive, no RAID or any other security) formatted in NTFS, everything is working. This is only the Lacie 2big drive, on this installation of Kubuntu, which is not working.

And last detail, before installing Kubuntu 10.04 RC, I upgraded Kubuntu 9.10 to Kubuntu 10.04 Beta 2, and it was not working either. I don'T remember if it was working on Kubuntu 9.10 before the upgrade.

Thank you for your help! :-)

---

### Post by P-Hell on 2010-04-24
If this can help, I found this method in [this post](http://ubuntuforums.org/showpost.php?p=8814340&postcount=7). Unplug the disk, use the *sudo partprobe* command. Plug the disk, use the command again. It worked for me.

I just hope I won't have to do this after every restart... :-P

---

### Post by FenwayFrank on 2010-04-25
Thanks but, no, still not seeing it.  Not with fdisk either.

I moved the drive to a different enclosure and may be getting closer.  It's running into something causing a backtrace dump:
~~~~
```
Apr 25 15:53:31 frank-laptop kernel: [ 3971.030122] usb 2-2: new high speed USB device using ehci_hcd and address 5
Apr 25 15:53:32 frank-laptop kernel: [ 3971.184368] usb 2-2: configuration #1 chosen from 1 choice
Apr 25 15:53:32 frank-laptop kernel: [ 3971.184970] scsi7 : SCSI emulation for USB Mass Storage devices
Apr 25 15:53:37 frank-laptop kernel: [ 3976.181625] scsi 7:0:0:0: Direct-Access     Maxtor A RES C64K         0811 PQ: 0 ANSI: 0
Apr 25 15:53:37 frank-laptop kernel: [ 3976.182587] sd 7:0:0:0: Attached scsi generic sg2 type 0
Apr 25 15:53:37 frank-laptop kernel: [ 3976.188452] sd 7:0:0:0: [sdb] 80295529 512-byte logical blocks: (41.1 GB/38.2 GiB)
Apr 25 15:53:37 frank-laptop kernel: [ 3976.189699] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
Apr 25 15:53:37 frank-laptop kernel: [ 3976.191946] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
Apr 25 15:54:08 frank-laptop kernel: [ 3976.191961]  sdb:
Apr 25 15:54:08 frank-laptop kernel: [ 4007.130118] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:54:39 frank-laptop kernel: [ 4038.130146] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:55:10 frank-laptop kernel: [ 4069.130110] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:55:41 frank-laptop kernel: [ 4100.132596] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:56:12 frank-laptop kernel: [ 4131.130117] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:56:43 frank-laptop kernel: [ 4162.130094] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:56:43 frank-laptop kernel: [ 4162.284119] sd 7:0:0:0: [sdb] Unhandled error code
Apr 25 15:56:43 frank-laptop kernel: [ 4162.284128] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Apr 25 15:56:43 frank-laptop kernel: [ 4162.284148] __ratelimit: 102 callbacks suppressed
Apr 25 15:57:14 frank-laptop kernel: [ 4193.130113] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:57:45 frank-laptop kernel: [ 4224.130119] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:58:16 frank-laptop kernel: [ 4255.130132] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:58:47 frank-laptop kernel: [ 4286.134471] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:59:18 frank-laptop kernel: [ 4317.130122] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880156] async/0       D 0000000000000000     0  3604      2 0x00000000
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880167]  ffff88007d915ad0 0000000000000046 ffff8800b9ecbf40 0000000000015880
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880180]  ffff880087dbb110 0000000000015880 0000000000015880 0000000000015880
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880189]  0000000000015880 ffff880087dbb110 0000000000015880 0000000000015880
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880200] Call Trace:
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880217]  [<ffffffff810da740>] ? sync_page+0x0/0x50
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880228]  [<ffffffff8152ab18>] io_schedule+0x28/0x40
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880236]  [<ffffffff810da77d>] sync_page+0x3d/0x50
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880245]  [<ffffffff8152b247>] __wait_on_bit+0x57/0x80
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880253]  [<ffffffff810da8ee>] wait_on_page_bit+0x6e/0x80
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880263]  [<ffffffff81078a70>] ? wake_bit_function+0x0/0x40
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880272]  [<ffffffff810dc15e>] read_cache_page+0x4e/0x60
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880282]  [<ffffffff8117e16b>] read_dev_sector+0x2b/0xa0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880290]  [<ffffffff8117f265>] adfspart_check_ICS+0x25/0x190
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880299]  [<ffffffff8152a1d1>] ? printk+0x3c/0x43
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880308]  [<ffffffff8117ea23>] check_partition+0x133/0x190
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880317]  [<ffffffff8117eb62>] rescan_partitions+0xe2/0x2f0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880327]  [<ffffffff81321324>] ? get_device+0x14/0x20
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880337]  [<ffffffff8134a45c>] ? sd_open+0x7c/0x1f0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880346]  [<ffffffff8114d244>] __blkdev_get+0x184/0x3a0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880355]  [<ffffffff8114d46b>] blkdev_get+0xb/0x10
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880363]  [<ffffffff8117e33d>] register_disk+0x15d/0x180
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880373]  [<ffffffff8126c8d7>] add_disk+0x87/0x160
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880381]  [<ffffffff8134d252>] sd_probe_async+0x122/0x200
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880392]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880401]  [<ffffffff8107f700>] ? async_thread+0x0/0xe0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880409]  [<ffffffff8107f5f5>] run_one_entry+0x75/0x180
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880417]  [<ffffffff8107f75d>] async_thread+0x5d/0xe0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880426]  [<ffffffff81053990>] ? default_wake_function+0x0/0x10
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880434]  [<ffffffff8107f700>] ? async_thread+0x0/0xe0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880443]  [<ffffffff81078646>] kthread+0xa6/0xb0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880452]  [<ffffffff8101316a>] child_rip+0xa/0x20
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880461]  [<ffffffff810785a0>] ? kthread+0x0/0xb0
Apr 25 15:59:22 frank-laptop kernel: [ 4321.880468]  [<ffffffff81013160>] ? child_rip+0x0/0x20
Apr 25 15:59:49 frank-laptop kernel: [ 4348.130158] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 15:59:49 frank-laptop kernel: [ 4348.281495] sd 7:0:0:0: [sdb] Unhandled error code
Apr 25 15:59:49 frank-laptop kernel: [ 4348.281504] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Apr 25 16:00:20 frank-laptop kernel: [ 4379.130148] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Apr 25 16:00:51 frank-laptop kernel: [ 4410.132616] usb 2-2: reset high speed USB device using ehci_hcd and address 5

```

---

### Post by cmcanulty on 2010-05-20
Same  thing here, WD & maxtor won'tmount in 10.04 this is a major bug that needs fixing

---

### Post by nowell29 on 2010-05-20
Not sure if this is entirely related, but I had this issue with 9.10 as well.  Fresh install of 10.04 as of last night, and mounting is hit and miss sometimes.  Last night it mounted fine, but this morning it will not.

Interesting observation though.  This drive is a 1TB NTFS Iomega drive.  I am using Xubuntu.  When I plug it in, it shows up in lsusb, but it will not come up in thunar.  Then, if I run sudo thunar, it shows up as mounted, and will only let user root play with it? 

Why would it be coming up only in root permissions now and then??

I would assume some or most of you are using gnome, you might see if a "sudo nautilus" shows it as mounted.  I find this inconsistancy odd and frustrating.

---

