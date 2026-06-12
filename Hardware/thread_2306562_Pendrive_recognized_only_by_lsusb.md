---
title: "Pendrive recognized only by lsusb"
date: 2015-12-16
forum: Hardware
---

### Post by GrejnoM on 2015-12-16
Hi everyone,

First things first, I apologize for my english, as it might be a bit wonky at times. I also apologize for any terms that I might have used incorrectly - I'm still new to Linux.

Also, I'm sorry if this isn't the right place for this issue, as it might be more of a general hardware issue, rather than an Ubuntu/GNU Linux one. But I'm running out of options, and I'm just hoping that fixing it with the help of Linux might be possible.

_**The gist of the issue:**_ 

My pendrive 'died', lsusb reports it fine, but it's not mounting and GParted can't see it.

_**The backstory:**_

I recently (as in, 3 hours ago) got myself a Sandisk Extreme 64GB, just due to the promised r/w speeds, as I wanted to get myself a portable, persistent Linux install to carry on me at all times[SIZE=1], and to prove my... incompetent friends that their computer doesn't need replacing because Windows won't boot[/SIZE]. 

First thing that I did after unboxing it was run some benchmarks. Ended up with about 170 write/165 read, and while the read speed was quite far from what [ UserBenchmark usually reported]("http://usb.userbenchmark.com/SanDisk-Extreme-USB-30-64GB/Rating/1459"), I didn't pay too much attention to it, as it still was faster than my Sata II drive.

So the next thing was just to get Linux onto it. I was running on my Windows at the time, so I tried to do so with the UniversalUSBInstaller. 

Halfway through the process, it hanged. I looked into "My Computer" - the pendrive icon was there, but the bar indicating drive usage was gone - as if the drive wasn't formatted at all. Trying to "safely remove the device" didn't work - literally nothing happened. The smart thing to do would have been to shut down the PC with the drive still inside, as it was obviously stuck in the middle of the operation, and shutting down the pc would put a stop to that. But I just yanked it out.

After reinserting it, there was literally no response from Windows. So I plugged it into my Linux/Ubuntu laptop. No response here as well. So I ran some commands in hope of getting more info, and perhaps fixing the issue.

**_The important stuff:_**

My linux machine is a Lenovo G500s, running Ubuntu 15.04:

```
dedged@dedged-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid
dedged@dedged-ubuntu:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Model name:            Intel(R) Core(TM) i3-3120M CPU @ 2.50GHz
Stepping:              9
CPU MHz:               2474.707
CPU max MHz:           2500,0000
CPU min MHz:           1200,0000
BogoMIPS:              4988.30
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
NUMA node0 CPU(s):     0-3



```

Windows tries to mount it only upon the first insertion, when it tries to install the drivers - but that's all it ever tries to do. None of the machines in my house, no matter the OS, can access the pendrive.

GParted doesn't give me the option to select the pendrive.

fdisk -l - detects only my primay HDD, no traces of the pendrive.

```
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd9fa2484


Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda4             2046 1953523711 1953521666 931,5G  f W95 Ext'd (LBA)
/dev/sda5        425152512 1264013311  838860800   400G  7 HPFS/NTFS/exFAT
/dev/sda6  *      20973568  425150463  404176896 192,7G 83 Linux
/dev/sda7             4096    4198399    4194304     2G 83 Linux
/dev/sda8          4200448   20971519   16771072     8G 82 Linux swap / Solaris
/dev/sda9       1264015360 1280792575   16777216     8G 82 Linux swap / Solaris
/dev/sda10      1280794624 1953523711  672729088 320,8G 83 Linux


Partition 5 does not start on physical sector boundary.
```

Same goes for lsblk - it outputs only /dev/sda and sr0.

```
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda       8:0    0 931,5G  0 disk 
&#9500;&#9472;sda4    8:4    0     1K  0 part 
&#9500;&#9472;sda5    8:5    0   400G  0 part /media/dedged/Everything
&#9500;&#9472;sda6    8:6    0 192,7G  0 part /
&#9500;&#9472;sda7    8:7    0     2G  0 part /boot
&#9500;&#9472;sda8    8:8    0     8G  0 part 
&#9500;&#9472;sda9    8:9    0     8G  0 part 
&#9492;&#9472;sda10   8:10   0 320,8G  0 part 
sr0      11:0    1  1024M  0 rom  
```

I tried running lsusb - it detected the pendrive.

```
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 004: ID 8087:07da Intel Corp. 
**Bus 003 Device 003: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive**
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0bda:5728 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I tried lsusb -v, and that, too, gave me a decent description of the device.
*Note: I haven't done this before it crapped out on me, so I can't tell if the output is any different.*

```
Bus 003 Device 003: ID 0781:5580 SanDisk Corp. SDCZ80 Flash DriveDevice Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0781 SanDisk Corp.
  idProduct          0x5580 SDCZ80 Flash Drive
  bcdDevice            0.10
  iManufacturer           1 SanDisk
  iProduct                2 Extreme
  iSerial                 3 AA011117150448510335
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
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
        bInterval              20
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              20
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat           7 micro seconds
    bU2DevExitLat         101 micro seconds
Device Status:     0x0000
  (Bus Powered)

```

I tried looking for changes in /dev before and after inserting the pendrive - the only thing that changes is stuff inside /dev/char, which in turn points to /dev/bus/usb/002/00X and ../003/00X, depending on the USB port that I plug the pendrive into (002/00X is USB 3.0, 003/00X is USB 2.0).

Out of despair, I tried just mounting /dev/bus/usb/00x/00x, but, to no-ones surprise...

```

#189:264 was the only file that changed upon re-inserting the pendrive, and it pointed at /dev/bus/usb/003/009 

sudo mount /dev/char/189:264 /media/haba
mount:  /dev/bus/usb/003/009 is not a block device
```

...it didn't work. 

At that point I tried to reboot the PC with the pendrive still connected - it hangs on POST for a good minute, or until I remove the pendrive. If I go into BIOS and connect the pendrive, the same thing happens - it hangs there for a good minute or so, or until I remove it.

That's all of the ideas that I had. I'm slowly leaning towards the idea that in some magical way the memory chip burned out, while the rest of the pendrive stayed intact.

If anyone has any ideas as to what else I could do to try and salvage it, then I'd greatly appreciate any help.

---

### Post by Hydranix on 2015-12-16
Ok so it's dead as far as we can tell. Don't worry though, there's a good chance it can be saved. It will require using Windows XP or Windows 7 though. (XP preferred, but 7 usually works ok). A strange requirement, I know.


I'm curious how you went about benchmarking the USB flash drive (henceforth UFD). Hopefully whatever method you used was safe for UFDs. Some tests have been known and shown to cause premature failure in UFDs due to their simple controller firmware not doing proper wear leveling. (Benchmark software will make continuous and heavy read/write cycles to only one "sector" of the flash chip causing it to fail. If I have the slightest clue about the inner-workings of flash memory, I'd say its like breaking the first link in a chain and losing the whole chain. I could be wrong about that stuff, but I know how to fix em.


Ok so you provided some good information. First thing I saw was that the device requires 200ma current. Second is that its a SanDisk sdcz80.

I found a picture of it cracked open, it saves you the trouble of having to do so since the controller is branded by SanDisk.

You need to run these tools from Windows with the drive plugged in and post back everything they say. This hopefully should uncover the controller model and what NAND chip it has in it.

(I know they look a little scary, but trust me, they're clean of viruses and do exactly what they say.)
[http://flashboot.ru/files/file/361/download/chipeasy_en_v1566_3df/](http://flashboot.ru/files/file/361/download/chipeasy_en_v1566_3df/)
[http://flashboot.ru/files/file/448/download/chipgenius_v4_00_0807_b05/](http://flashboot.ru/files/file/448/download/chipgenius_v4_00_0807_b05/)
[http://flashboot.ru/files/file/362/download/usbflashinfo_v75_044/](http://flashboot.ru/files/file/362/download/usbflashinfo_v75_044/)

If need to reach me in case I don't come back soon enough, my email is Hydranix at GMX dot com

---

### Post by GrejnoM on 2015-12-19
> **Hydranix said:**
> I'm curious how you went about benchmarking the USB flash drive (henceforth UFD). Hopefully whatever method you used was safe for UFDs. Some tests have been known and shown to cause premature failure in UFDs due to their simple controller firmware not doing proper wear leveling. (Benchmark software will make continuous and heavy read/write cycles to only one "sector" of the flash chip causing it to fail. If I have the slightest clue about the inner-workings of flash memory, I'd say its like breaking the first link in a chain and losing the whole chain. I could be wrong about that stuff, but I know how to fix em.

Allright, thanks for the reply! I used HD Tune on Windows and [a simple Linux script]("http://www.binarytides.com/linux-test-drive-speed/"), which just copied over a file of set size, filed with zeros:

```

#write speed, a file 81.92 megabytes in size
dd if=/dev/zero of=/media/sandisk/testfile bs=8k count=10000

#write to disk & clear cache
sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches"

#read speed 
dd if=/media/sandisk/testfile of=/dev/null bs=8k

```

As for the programs, here's what they gave me:

_**GetFlashInfo, USB 3.0:**_
```
Volume: H:Controller: SanDisk
Possible Memory Chip(s): Not available
VID: 0781
PID: 5580
Manufacturer: SanDisk
Product: Extreme
Query Vendor ID: SanDisk 
Query Product ID: Extreme         
Query Product Revision: 0001
Physical Disk Capacity: 0 Bytes
Windows Disk Capacity:  0 Bytes
Internal Tags: BW4B-AAHJ
USB Version: 3.00
Max. Power: 100 mA
ContMeas ID: F38C-01-00
Microsoft Windows 7 SP1 x64
------------------------------------
http://www.antspec.com/usbflashinfo/
Program Version: 7.5.0.480

```

And the output varied slightly on USB 2.0:
```
Max. Power: 200 mA
ContMeas ID: F38C-02-00
```
[U][B]
ChipGenius, USB 3.0:[/B][/U]
```
Description: [H:]USB Mass Storage Device(SanDisk Extreme)Device Type:        Mass Storage Device


Protocal Version: USB 3.00
Current Speed: Super Speed
Max Current: 400mA


USB Device ID: VID = 0781 PID = 5580
Serial Number: AA011117150448510335


Device Vendor: SanDisk
Device Name: Extreme
Device Revision: 0010


Manufacturer: SanDisk
Product Model: Extreme
Product Revision: 0001


Controller Part-Number: Unknown
```

And again, on USB 2.0 it reported different max current: 
```
Max Current: 200mA
```

_**ChipEasy, USB 3.0:**_
```
Logical drive   : H:\            Capacity:  0.0GDevice ID       : VID = 0781     PID = 5580
Device SN       : AA011117150448510335
Device version  : 0001


Device vendor   : SanDisk
Device model    : Extreme
Protocol        : USB3.0
Max power       : 100mA


Partition type  :                Device active   : 
Aligned state   : Misaligned


Controller      : SanDisk
Controller model: 


Tools           :  
OS Version      : Windows 7 Professional Service Pack 1
Update Status   : The current version is the latest version! 
```

It gave out a bit more info when plugged into USB 2.0:
```

Device vendor   : SanDisk
Device model    : Extreme
**Protocol        : USB2.0**
**Max power       : 200mA**

Partition type  :                Device active   : 
Aligned state   : Misaligned

**Controller      : Chipsbank**
**Controller model: CBManDisk**
**FW Date         : Extr.e .**
```

---

