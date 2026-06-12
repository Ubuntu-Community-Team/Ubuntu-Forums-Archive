---
title: "slow HDD  :-(  no DMA??"
date: 2008-08-10
forum: General Help
---

### Post by nitish_nit555 on 2008-08-10
Hi.......

I am using ubuntu 8.04

i have an IDE disk

~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

but my hard disk is listed as SATA:(

$ sudo fdisk -l
[sudo] password for nitish: 

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb225b225

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        4009    11719417+   c  W95 FAT32 (LBA)
/dev/sda3            4010        4799     6345675   83  Linux
/dev/sda4            4800        4870      570307+  82  Linux swap / Solaris

The main problem is this:-

$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 4870/255/63, sectors = 78242976, start = 0

and this:

~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   642 MB in  2.00 seconds = 320.61 MB/sec
 Timing buffered disk reads:   58 MB in  3.04 seconds =  19.05 MB/sec

hard disk is very slow.
the overall performance is very bad.

how do can i enable DMA on my IDE disk??

---

### Post by Vivaldi Gloria on 2008-08-10
> **nitish_nit555 said:**
> how do can i enable DMA on my IDE disk??


To see the state of it use

```
sudo blktool /dev/sda dma
```

To turn dma on use

```
sudo blktool /dev/sda dma on
```

---

### Post by nitish_nit555 on 2008-08-11
I tried blktool It is also not working.....


```
~$ sudo blktool /dev/sda dma on
[sudo] password for nitish: 
HDIO_SET_DMA: Inappropriate ioctl for device
```

```
:~$ sudo blktool /dev/sda dma
HDIO_GET_DMA: Inappropriate ioctl for device

```

---

### Post by Vivaldi Gloria on 2008-08-11
FYI, every disk is sdx in ubuntu. 

Sorry, but don't know what you can do. Report a bug maybe.

---

### Post by nitish_nit555 on 2008-08-11
It is Bug that have been already reported to launchpad.net

but i found no solution to this problem.

I have google it too much but their is no solution

Is this bug can not be fixed???

I found an article on this topic but i can not understand it all..

[http://linux-ata.org/faq.html](http://linux-ata.org/faq.html)

---

### Post by Bucky Ball on 2008-08-11
> **nitish_nit555 said:**
> I tried blktool It is also not working.....


```
~$ sudo blktool /dev/sda dma on
[sudo] password for nitish: 
HDIO_SET_DMA: Inappropriate ioctl for device
``````
:~$ sudo blktool /dev/sda dma
HDIO_GET_DMA: Inappropriate ioctl for device

```

Ditto

---

### Post by nitish_nit555 on 2008-08-12
Please !!!


any help for me..................


Do I need to downgrade to an older linux kernel?




.

---

### Post by Bucky Ball on 2008-08-12
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/102316](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/102316)

This page says the problem was fixed in Gutsy (last version before Hardy).

No, older kernel will not solve the problem, in fact possibly worsen it!

This page might give you some clues, even though about cd/dvd;

[http://menpro.blogspot.com/2008/04/kaffeine-cant-check-dma-mode-permission.html](http://menpro.blogspot.com/2008/04/kaffeine-cant-check-dma-mode-permission.html)

---

### Post by nitish_nit555 on 2008-08-12
This problem is not like that.

This is problem is related to intel combined mode and libata driver

see this page

linux-ata.org/faq.html

---

### Post by Bucky Ball on 2008-08-13
Well, if you know that, the page you posted looks like you have a solution I will consider this thread solved.
Bye

---

### Post by nitish_nit555 on 2008-08-13
No this will not solve my problem.

I tried to boot ubuntu with combined_mode=libata, 

combined_mode=ide, sda=none, sda=noprobe but no effect

I also tried atapi_enabled=1

always hdparm give me same answer.

.

---

### Post by Bucky Ball on 2008-08-13
> This problem is not like that.

This is problem is related to intel combined mode and libata driver

see this page

linux-ata.org/faq.html

If that page didn't fix, perhaps that is not your problem. Does 

```
sudo blkid
```give you anything?

Have you tried these two things from that page you posted before?

[quote=http://linux-ata.org/faq.html]**Recommended** (where BIOS permits): Change BIOS IDE mode from "legacy" or "combined" mode to "AHCI" (recommended), "RAID" or "native".

 Disable CONFIG_IDE, and permit libata to run all your IDE and SATA ports.[/quote]

---

