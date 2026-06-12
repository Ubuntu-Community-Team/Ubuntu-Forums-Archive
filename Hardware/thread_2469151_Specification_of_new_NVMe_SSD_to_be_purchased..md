---
title: "Specification of new NVMe SSD to be purchased."
date: 2021-11-21
forum: Hardware
---

### Post by satimis on 2021-11-21
PC HDDs config:
==========
1TB NVMe SSD for running OS
4TB WD HDD for data storage

Now NVMe SSD is having insufficient space and I'm prepared to buy a new 2TB NVMe SSD.

Running following commands I found;

1)
$ sudo lsblk -e7```

NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                     8:0    0   3.7T  0 disk 
&#9492;&#9472;sda1                  8:1    0   3.7T  0 part 
nvme0n1               259:0    0 953.9G  0 disk 
&#9500;&#9472;nvme0n1p1           259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2           259:2    0 953.4G  0 part 
  &#9500;&#9472;ubuntu--vg-root   253:0    0 930.4G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 253:1    0   976M  0 lvm  [SWAP]
  
```
 
 
2a)
$ sudo hdparm -I /dev/sda | grep Serial ```

                     &#9474;        Serial Number:      V6JA7AER                                            &#9474;        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SAT&#9474;A Rev 2.5, SATA Rev 2.6, SATA Rev 3.0; Revision: ATA8-AST T13 Project D1697 Revi&#9474;sion 0b   
``` 

2b)
$ sudo hdparm -I /dev/nvme0n1 | grep Serial```

 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device

```             

2c)                     
$ lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,MODEL | grep nvme0n1```

nvme0n1                                                                  953.9G INTEL SSDPEKNW010T8
&#9500;&#9472;nvme0n1p1           vfat              /boot/efi                          512M 
&#9492;&#9472;nvme0n1p2           LVM2_member                         

```                  

3)
$ sudo lshw -short -C disk```

H/W path                Device          Class          Description
==================================================================
/0/100/1.6/0/0/1        /dev/nvme0n1    disk           1024GB NVMe namespace
/0/7/0.0.0              /dev/sda        disk           4TB HGST HUS726T4TAL

```

Motherboard
========
$ sudo dmidecode -t 2```

# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: PRIME X570-P
        Version: Rev X.0x
        Serial Number: 190753869002923
        Asset Tag: Default string
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Default string
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

```

Please advise what will be the specification of the new 2TB NVMe SSD to be purchased.

Thanks in advance.

Regards

---

### Post by Dennis N on 2021-11-21
Your current drive model is a QLC drive. These are the least expensive X4 drives for given capacity. But, they are slower and less durable than TLC drives, especially when writing to the disk. I would opt for a TLC drive myself. There are pros and cons. Read:
[Article on pros and cons of QLC flash]("https://www.howtogeek.com/428869/ssds-are-getting-denser-and-slower-thanks-to-qlc-flash/")
Other than that, be sure it has 4 channels (X 4) and not 2 (X 2) which would slow it down by 1/2. Most sold are (X 4).
Much depends on your use case.

---

### Post by oldfred on 2021-11-21
What does this show?
udisksctl status
and/or nvme, you may need to install 
sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list

Have you updated firmware on SSD & motherboard?
What does motherboard manual say about NVMe drives. 
Some new ones now support more than one, but may prevent a SATA port from working or not have full speed on second one.

Do not know LVM, but those that do always want the LVM commands to see details.
sudo pvs
sudo vgs
sudo lvs

I upgraded my M.2 SATA SSD to larger NVMe SSD and put M.2 SATA drive in an external enclosure. Now sold on external SSD (really fast) over flash drives (really slow). Not sure that you get any extra speed thru USB3 adapter fro NVMe, perhaps with USB-C to take more advantage of NVMe's faster speeds.

---

### Post by satimis on 2021-11-21
Hi oldfred,

Thanks for your advice.

This AMD Ryzen 5 PC was built about 3~4 years ago.  I have been planning to build a new AMD Ryzen 7/9 PC sometimes but unable to find spare time.

> **oldfred said:**
> What does this show?
udisksctl status
and/or nvme, you may need to install 
sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list

$ udisksctl status```

MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
INTEL SSDPEKNW010T8       002C      BTNH93310UXC1P0B     nvme0n1 
HGST HUS726T4TALE6L4      VKGAW41G  V6JA7AER             sda     

```

$ sudo nvme list```

Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     BTNH93310UXC1P0B     INTEL SSDPEKNW010T8                      1           1.02  TB /   1.02  TB    512   B +  0 B   002C    

```

The running NVME SSD is pcie package.  Pls refers to attached photo

How can I check the spec of the running NVME SSD, pcie 3.0 or 4.0 ?

> 
Have you updated firmware on SSD & motherboard?
What does motherboard manual say about NVMe drives. 
Some new ones now support more than one, but may prevent a SATA port from working or not have full speed on second one.

Sorry I couldn't recall. I haven't updated firmware for long time.  Do I need to do it regularily?  If YES, please advise HOW?  Thanks

Where can I check?  Hereinbelow is ASUS motherboard spec URL;

ASUS PRIME X570-P
[https://www.asus.com/Motherboards-Components/Motherboards/PRIME/PRIME-X570-P/techspec/](https://www.asus.com/Motherboards-Components/Motherboards/PRIME/PRIME-X570-P/techspec/)

Storage```

AMD Ryzen™ 5000 Series/ 3000 Series Desktop Processors :
1 x M.2_1 socket 3, with M Key, Type 2242/2260/2280 (PCIE 4.0 x4 and SATA modes) storage devices support
AMD Ryzen™ 5000 G-Series/ 4000 G-Series/ 3000 G-Series/ 2000 Series/ 2000 G-Series Desktop Processors :
1 x M.2_1 socket 3, with M Key, Type 2242/2260/2280 (PCIE 3.0 x4 and SATA modes) storage devices support
AMD X570 chipset :
1 x M.2_2 socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
6 x SATA 6Gb/s port(s)
Support Raid 0, 1, 10

```

Pls refers to motherboard photo

> 
Do not know LVM, but those that do always want the LVM commands to see details.
sudo pvs
sudo vgs
sudo lvs


$ sudo pvs```

  PV             VG        Fmt  Attr PSize    PFree  
  /dev/nvme0n1p2 ubuntu-vg lvm2 a--  <953.37g <22.05g

```

$ sudo vgs```

  VG        #PV #LV #SN Attr   VSize    VFree  
  ubuntu-vg   1   2   0 wz--n- <953.37g <22.05g

```

$ sudo lvs```

  LV     VG        Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubuntu-vg -wi-ao---- <930.37g                                                    
  swap_1 ubuntu-vg -wi-ao----  976.00m  

```

> 
I upgraded my M.2 SATA SSD to larger NVMe SSD and put M.2 SATA drive in an external enclosure. Now sold on external SSD (really fast) over flash drives (really slow). Not sure that you get any extra speed thru USB3 adapter fro NVMe, perhaps with USB-C to take more advantage of NVMe's faster speeds.
Does pcie SSD package have external enclosure?

Thanks

Regards

---

### Post by satimis on 2021-11-21
> **Dennis N said:**
> Your current drive model is a QLC drive. These are the least expensive X4 drives for given capacity. But, they are slower and less durable than TLC drives, especially when writing to the disk. I would opt for a TLC drive myself. There are pros and cons. Read:
[Article on pros and cons of QLC flash]("https://www.howtogeek.com/428869/ssds-are-getting-denser-and-slower-thanks-to-qlc-flash/")
Other than that, be sure it has 4 channels (X 4) and not 2 (X 2) which would slow it down by 1/2. Most sold are (X 4).
Much depends on your use case.
Hi Dennis,

Thanks for your advice.

My NVMe SSD is pcie package.  Pls see attached photo

How can I check the spec of the running NVME SSD, pcie 3.0 or 4.0 ?

Edit
===
This PC is running Oracle VirtualBox with Ubuntu20.04 as host.

After adding a new 2TB NVME pcie SSD I'll use the old one to running KVM/QEMU.  I need speed.

Regards

---

### Post by oldfred on 2021-11-21
Do not know Intel, but quick Google search said this site had firmware.
[https://www.intel.com/content/www/us/en/support/articles/000017245/memory-and-storage.html](https://www.intel.com/content/www/us/en/support/articles/000017245/memory-and-storage.html)

[https://www.intel.com/content/www/us/en/download/17903/intel-ssd-firmware-update-tool.html](https://www.intel.com/content/www/us/en/download/17903/intel-ssd-firmware-update-tool.html)

You compare the FW rev (firmware revision) number shown in nvme or udisksctl output. And then see if they have a newer one and how to install it.
With my Samsung it was a bootable ISO that was old school. Looked like an old DOS screen with just one update for my model NVMe drive.

To convert SATA SSD to external I had to buy a external enclosesure/adapter. Was inexpensive, but I noted the NVMe cases were more expensive. I do not think I would buy a NVMe drive to use as an external as extra speed would not be available. But since you will have one, then worthwhile?

Search on your model:
[https://www.intel.com/content/www/us/en/products/sku/149407/intel-ssd-660p-series-1-0tb-m-2-80mm-pcie-3-0-x4-3d2-qlc/specifications.html](https://www.intel.com/content/www/us/en/products/sku/149407/intel-ssd-660p-series-1-0tb-m-2-80mm-pcie-3-0-x4-3d2-qlc/specifications.html)
PCIe 3.0 x4, NVMe

---

### Post by Dennis N on 2021-11-22
To get the information on your Intel drive, I googled the model number you showed in your output. It's PCIe 3.0 x4, NVMe QLC but the indicated read and write speeds are just 1800 MB/sec. A PCIe 3.0 x4 TLC drive would be rated nearly twice as fast.

The specs say the Intel 660p is a PCIe 3.0 x4, NVMe device. You can use PCIe 3.0 devices in a PCIe 4.0 slot, but it will work at PCIe 3.0 speed.

The 4.0 x 4 drives are going to be a lot more expensive for a given capacity.

If you are using a SATA drive as well, copying stuff from the NVMe drive to the SATA would be limited to the SATA drive speed. A SATA SSD max speed is around 500-600 MB/sec.

---

### Post by satimis on 2021-11-22
> **Dennis N said:**
> To get the information on your Intel drive, I googled the model number you showed in your output. It's PCIe 3.0 x4, NVMe QLC but the indicated read and write speeds are just 1800 MB/sec. A PCIe 3.0 x4 TLC drive would be rated nearly twice as fast.

The specs say the Intel 660p is a PCIe 3.0 x4, NVMe device. You can use PCIe 3.0 devices in a PCIe 4.0 slot, but it will work at PCIe 3.0 speed.

According to my recollection my NVME pcie SSD is pcie 3.0 ?  How can I check it on Terminal?  Thanks

> 
The 4.0 x 4 drives are going to be a lot more expensive for a given capacity.
Apart from cost is there pcie 4.0 x 4 slot on my motherboard?

Storage```

AMD Ryzen™ 5000 Series/ 3000 Series Desktop Processors :
1 x M.2_1 socket 3, with M Key, Type 2242/2260/2280 (PCIE 4.0 x4 and SATA modes) storage devices support
AMD Ryzen™ 5000 G-Series/ 4000 G-Series/ 3000 G-Series/ 2000 Series/ 2000 G-Series Desktop Processors :
1 x M.2_1 socket 3, with M Key, Type 2242/2260/2280 (PCIE 3.0 x4 and SATA modes) storage devices support
AMD X570 chipset :
1 x M.2_2 socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
6 x SATA 6Gb/s port(s)
Support Raid 0, 1, 10

```

I'm running Oracle VirtualBox here and I need speed.  Is there any advantage on running pcie 4.0 x 4 SSD ?

> 
If you are using a SATA drive as well, copying stuff from the NVMe drive to the SATA would be limited to the SATA drive speed. A SATA SSD max speed is around 500-600 MB/sec.
I only have one 4TB WD SATA HDD for data storage.  There is no OS running on this HDD.  Speed is not important

Regards

---

### Post by satimis on 2021-11-22
> **oldfred said:**
> Do not know Intel, but quick Google search said this site had firmware.
[https://www.intel.com/content/www/us/en/support/articles/000017245/memory-and-storage.html](https://www.intel.com/content/www/us/en/support/articles/000017245/memory-and-storage.html)

[https://www.intel.com/content/www/us/en/download/17903/intel-ssd-firmware-update-tool.html](https://www.intel.com/content/www/us/en/download/17903/intel-ssd-firmware-update-tool.html)

You compare the FW rev (firmware revision) number shown in nvme or udisksctl output. And then see if they have a newer one and how to install it.
With my Samsung it was a bootable ISO that was old school. Looked like an old DOS screen with just one update for my model NVMe drive.

$ udisksctl status```

MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
INTEL SSDPEKNW010T8       002C      BTNH93310UXC1P0B     nvme0n1 
HGST HUS726T4TALE6L4      VKGAW41G  V6JA7AER             sda

```

I suppose;
1)  002C is the firmware version of my NVMe pcie SSD
2)  BTNH93310UXC1P0B is the serial number of my NVMe pcie SSD

But I couldn't re-confirm the firmware version according to following document;
Find the Firmware Version for Your Intel® Solid State Drive 
[https://www.intel.com/content/www/us/en/support/articles/000005558/memory-and-storage.html](https://www.intel.com/content/www/us/en/support/articles/000005558/memory-and-storage.html)

-> Expand all

running following commands on Terminal as advised on the said document;
1)
$ sudo fdisk -l | more```

.....
Disk /dev/nvme0n1: 953.89 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: INTEL SSDPEKNW010T8                     
Units: sectors of 1 * 512 = 512 bytes
....

```

2)
$ sudo hdparm -i /dev/nvme0n1```


/dev/nvme0n1:
 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device

```

Nor I can compare 002C, the firmware version of my NVMe pcie SSD with following URL;
[https://www.intel.com/content/www/us/en/support/articles/000017245/memory-and-storage.html](https://www.intel.com/content/www/us/en/support/articles/000017245/memory-and-storage.html)

-> Expand all

Because I couldn't find INTEL SSDPEKNW010T8 on that page, the disk model of my NVMe pcie SSD

> 
To convert SATA SSD to external I had to buy a external enclosesure/adapter. Was inexpensive, but I noted the NVMe cases were more expensive. I do not think I would buy a NVMe drive to use as an external as extra speed would not be available. But since you will have one, then worthwhile?
I don't have NVMe external enclosesure.  Nor I would consider converting my NVMe pcie SSD to external

> 
Search on your model:
[https://www.intel.com/content/www/us/en/products/sku/149407/intel-ssd-660p-series-1-0tb-m-2-80mm-pcie-3-0-x4-3d2-qlc/specifications.html](https://www.intel.com/content/www/us/en/products/sku/149407/intel-ssd-660p-series-1-0tb-m-2-80mm-pcie-3-0-x4-3d2-qlc/specifications.html)
PCIe 3.0 x4, NVMe
Thanks

Interface = PCIe 3.0 x4, NVMe 

According the specification of my motherboard ASUS PRIME X570-P

Storage```

AMD Ryzen™ 5000 Series/ 3000 Series Desktop Processors :
1 x M.2_1 socket 3, with M Key, Type 2242/2260/2280 (PCIE 4.0 x4 and SATA modes) storage devices support
AMD Ryzen™ 5000 G-Series/ 4000 G-Series/ 3000 G-Series/ 2000 Series/ 2000 G-Series Desktop Processors :
1 x M.2_1 socket 3, with M Key, Type 2242/2260/2280 (PCIE 3.0 x4 and SATA modes) storage devices support
AMD X570 chipset :
1 x M.2_2 socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
6 x SATA 6Gb/s port(s)
Support Raid 0, 1, 10

```
My motherboard supports PCIE 4.0 x4

So I can purchase;
Samsung 2TB 980 PRO M.2 2280 MZ-V8P2T0BW PCIe Gen 4.0 x4, NVMe 1.3c SSD

to install it on my motherboard ?

980 PRO PCIe 4.0 NVMe® SSD 2TB
[https://www.samsung.com/us/computing/memory-storage/solid-state-drives/980-pro-pcie-4-0-nvme-ssd-2tb-mz-v8p2t0b-am/](https://www.samsung.com/us/computing/memory-storage/solid-state-drives/980-pro-pcie-4-0-nvme-ssd-2tb-mz-v8p2t0b-am/)

Please advise.  Thanks

Regards

---

### Post by Dennis N on 2021-11-22
> **satimis said:**
> $ udisksctl status[code]
Interface = PCIe 3.0 x4, NVMe 

According the specification of my motherboard ASUS PRIME X570-P...My motherboard supports PCIE 4.0 x4

So I can purchase;
Samsung 2TB 980 PRO M.2 2280 MZ-V8P2T0BW PCIe Gen 4.0 x4, NVMe 1.3c SSD

to install it on my motherboard ?

980 PRO PCIe 4.0 NVMe® SSD 2TB
[https://www.samsung.com/us/computing/memory-storage/solid-state-drives/980-pro-pcie-4-0-nvme-ssd-2tb-mz-v8p2t0b-am/](https://www.samsung.com/us/computing/memory-storage/solid-state-drives/980-pro-pcie-4-0-nvme-ssd-2tb-mz-v8p2t0b-am/)

Please advise.  Thanks

Regards

Yes, that's going to be compatable. Probably the best you could get. Speed ratings from Samsung: Read/Write Speeds 7,000/5,100 MB/s (these are probably the maximums).
 
In fact, you have two m.2 slots on that motherboard from the illustration on the Asus product page. At least one should be PCIe 4.0.

---

### Post by satimis on 2021-11-22
> **Dennis N said:**
> Yes, that's going to be compatable. Probably the best you could get. Speed ratings from Samsung: Read/Write Speeds 7,000/5,100 MB/s (these are probably the maximums).
 
In fact, you have two m.2 slots on that motherboard from the illustration on the Asus product page. At least one should be PCIe 4.0.
Hi Dennis

I found the online schematic drawing of
ASUS PRIME X570-P motherboard
[https://gzhls.at/blob/ldb/0/6/1/6/4e113977bf1a2eeec37f9d3c277a4563734b.pdf](https://gzhls.at/blob/ldb/0/6/1/6/4e113977bf1a2eeec37f9d3c277a4563734b.pdf)

How can I mount the 2TB NVME pcie 4.0 SSD on the PCIe 4.0 slots ?  Pls see attached screenshots

Thanks

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Just found following YouTube video;
How to install Samsung 950 PRO M.2 SSD in a PCIe slot with a Lycom DT-120 M.2 to PCIe adapter
[https://www.youtube.com/watch?v=LDRm0Y8pNMo](https://www.youtube.com/watch?v=LDRm0Y8pNMo)

**[COLOR="#FF0000"]I have to buy a Lycom DT-120 M.2 to PCIe adapter[/COLOR]**


Regards

---

### Post by oldfred on 2021-11-22
If you have two M.2 slots, why would you need an adapter?
 I think that is only for those with one slot on motherboard.

---

### Post by satimis on 2021-11-22
> **oldfred said:**
> If you have two M.2 slots, why would you need an adapter?
 I think that is only for those with one slot on motherboard.
11  is M.2 Socket 3.  Is it for pcie 3.0 ?

Pls see attached screenshots

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
I found it.  Pls refers to attached screenshot - screenshot_socket3_55.png

For 3rd Gen AMD Ryzen™ Processors, the M.2_1 socket supports PCIe 4.0 x4 mode 
and SATA mode M Key design and type 2242 / 2260 / 2280 storage devices. 
•  For 2nd Gen AMD Ryzen™/2nd and 1st Gen AMD Ryzen™ with Radeon™ Vega 
Graphics Processors, the M.2_1 socket supports PCIe 3.0 x4 mode and SATA mode 
M Key design and type 2242 / 2260 / 2280 storage devices. 
•  The M.2_2 socket supports PCIe 4.0 x4 mode and SATA mode M Key design and 
type 2242 / 2260 / 2280 / 22110 storage devices.

To my understanding both M.2_1 and M.2_2 sockets support PCIe 4.0 x4 mode

Regards

---

### Post by Dennis N on 2021-11-22
> To my understanding both M.2_1 and M.2_2 sockets support PCIe 4.0 x4 mode

Well, M.2_1 could be PCIe 3.0x4 or 4.0x4 depending on the processor you are using. If its 3rd generation processor, then it's PCIe 4.0. Otherwise, it's PCIe 3.0.

The other socket M.2_2 is PCIe 4.0x4 for all the mentioned processors.

That's how I interpret what it says.

---

### Post by satimis on 2021-11-23
> **Dennis N said:**
> Well, M.2_1 could be PCIe 3.0x4 or 4.0x4 depending on the processor you are using. If its 3rd generation processor, then it's PCIe 4.0. Otherwise, it's PCIe 3.0.

The other socket M.2_2 is PCIe 4.0x4 for all the mentioned processors.

That's how I interpret what it says.

$ lscpu | more ```

Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   43 bits physical, 48 bits virtual
CPU(s):                          8
On-line CPU(s) list:             0-7
Thread(s) per core:              2
Core(s) per socket:              4
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       AuthenticAMD
CPU family:                      23
Model:                           24
Model name:                      AMD Ryzen 5 3400G with Radeon Vega Graphics
Stepping:                        1
Frequency boost:                 enabled
CPU MHz:                         1652.418
CPU max MHz:                     3700.0000
CPU min MHz:                     1400.0000
BogoMIPS:                        7386.09
Virtualization:                  AMD-V
....
....

```

1)
According to my CPU spec.
Whether I can use socket M.2_1 for PCIe 4.0x4 without loss in speed ?

2)
I can use socket M.2_2 for PCIe 4.0x4 without loss in speed, disregarding CPU ?

Thanks

Regards

---

### Post by Dennis N on 2021-11-23
> 1)
According to my CPU spec.
Whether I can use socket M.2_1 for PCIe 4.0x4 without loss in speed ?

2)
I can use socket M.2_2 for PCIe 4.0x4 without loss in speed, disregarding CPU ?


I'm not familiar with the AMD processors - all of mine are Intel. So you have to determine whether yours is considered 3rd generation. It might be so because of the 3XXX numbering. I'm not going to guess on that. Ask in a separate thread if you are not sure and can't figure it out by searching. Someone will know. 

If it's determined to be 3rd generation, then the answer to (1) would be yes and (2) would be yes. If it's not 3rd generation, then the answer to (1) is no - the PCIe 4.0 drive would function at PCIe 3.0 speed; and the answer for (2) is yes - the 4.0 drive would work at full 4.0 speed. Page I-19 in the user manual sets no restrictions on the M.2_2 slot based on the CPU.

---

### Post by Dennis N on 2021-11-23
Follow up: I googled on the drive model shown in your post number 15. Is this your processor described here?
[https://www.amd.com/en/products/apu/amd-ryzen-5-3400g](https://www.amd.com/en/products/apu/amd-ryzen-5-3400g)
If so, the box in the top illustration says "2nd generation"
That would mean an NVMe PCE 4.0 x 4 drive would need to be in the M.2_2 slot to function at 4.0 speed. That should not pose a problem - you only will have one PCIe 4.0 drive.

---

### Post by satimis on 2021-11-23
> **Dennis N said:**
> Follow up: I googled on the drive model shown in your post number 15. Is this your processor described here?
[https://www.amd.com/en/products/apu/amd-ryzen-5-3400g](https://www.amd.com/en/products/apu/amd-ryzen-5-3400g)
If so, the box in the top illustration says "2nd generation"
That would mean an NVMe PCE 4.0 x 4 drive would need to be in the M.2_2 slot to function at 4.0 speed. That should not pose a problem - you only will have one PCIe 4.0 drive.
Yes.

Thanks for your information

[B][COLOR="#FF0000"]A side question.
==============[/COLOR][/B]

I'm prepared purchasing;
Samsung 2TB 980 PRO M.2 2280 MZ-V8P2T0BW PCIe Gen 4.0 x4, NVMe 1.3c SSD

and connect it in M.2_2 slot

Which will be an easy and reliable way to migrate/dump all files from my old Intel 1TB PCIe Gen 3.0 x4 NVMe SSD

to it?

Thanks

Regards

---

### Post by Dennis N on 2021-11-23
> Which will be an easy and reliable way to migrate/dump all files from my old Intel 1TB PCIe Gen 3.0 x4 NVMe SSD to it? Do you mean cloning (making an exact copy)? I've never needed (or wanted) to do that, so I'm not qualified to advise. I suggest making a new thread with that question.

---

### Post by satimis on 2021-11-23
> **Dennis N said:**
> Do you mean cloning (making an exact copy)? I've never needed (or wanted) to do that, so I'm not qualified to advise. I suggest making a new thread with that question.
Noted and thanks

Regards

---

