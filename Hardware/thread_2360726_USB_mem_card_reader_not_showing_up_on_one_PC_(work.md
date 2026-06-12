---
title: "USB mem card reader not showing up on one PC (works others)"
date: 2017-05-07
forum: Hardware
---

### Post by efflandt on 2017-05-07
I got a USB 2.0 memory card reader, primarily because it includes a CF slot and I have CF from an old Nikon camera. I thought it didn't work because nothing shows up for it in lsusb or dmesg on my main PC when connected. But I discovered that it works fine on other computers. For example I used the card reader to install 64-bit 16.04 to 16 GB SDHC using an old HP Athlon64 3200+ (2 GHz) from 2004. And I can boot from SD in the card reader on that PC:```
Ubuntu 16.04 booted from 16 GB SD in card reader (Genesys):
Bus 001 Device 002: ID 05e3:0745 Genesys Logic, Inc. Logilink CR0012
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 04ca:0027 Lite-On Technology Corp. 
Bus 003 Device 002: ID 0461:4d65 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

In 64-bit Ubuntu 10.04 on hd (Genesys showed up after card reader connected):
Bus 003 Device 003: ID 04ca:0027 Lite-On Technology Corp.
Bus 003 Device 002: ID 0461:4d65 Primax Electronics, Ltd
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 05e3:0745 Genesys Logic, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```But on my main PC (Dell XPS 8100 from 2010) running 64-bit 16.10 there is no change in lsusb or dmesg when the USB card reader w/SD is connected. Yet a USB 3.0 64 GB PNY memory stick shows up fine inserted in same USB port.```
In 16.10 on trouble PC, whether card reader inserted or not:
Bus 002 Device 008: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 18e3:9106 Fitipower Integrated Technology Inc 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:0768 Microsoft Corp. Sidewinder X4
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

In 16.10 on trouble PC, with 64 GB PNY stick in same USB port:
Bus 002 Device 010: ID 154b:00d4 PNY 
Bus 002 Device 008: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 18e3:9106 Fitipower Integrated Technology Inc 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:0768 Microsoft Corp. Sidewinder X4
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I also booted live/install 16.04 from USB 3.0 memory stick and that sees nothing in lsusb or dmesg for the card reader w/SD. But maybe it is a BIOS issue because when I hit the hot key to select boot device, the card reader with installed system on SD does not show up as a choice. Could it possibly be a conflict with my built-in card reader (Fitipower internally connected to USB) which can read/write that 16 GB SD card with installed 16.04 just fine? The old PC that the reader works on also has internal multi-card reader, but on USB 1.0, not 2.0. On only that one computer the card reader does not even appear to power up (its LED is off) on a USB port that works fine for memory stick, Bluetooth dongle, portable hard drive, etc. Any ideas?

---

### Post by cary-proust on 2017-11-03
Hey folks,

Has anyone gotten this thing working? Very frustrating issue. Doesn't seem to work when I insert a sd card whereas any USB or compactflash works just fine. Is this just a case of Fitipower is just generic crap and I should look to a better manufacturer? I'm seriously considering a purchase of a new sd card reader and a baseball bat right now.

root@Starbug1:/dev#* lsusb*
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 152d:0567 JMicron Technology Corp. / JMicron USA Technology Corp. JMS567 SATA 6Gb/s bridge
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 258a:1007  
**Bus 003 Device 002: ID 18e3:9101 Fitipower Integrated Technology Inc All-in-1 Card Reader**
Bus 003 Device 007: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 006: ID 27b1:0001  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

root@Starbug1:/dev# *lspci*
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
05:01.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 01)

root@Starbug1:/dev# ls /dev/sd*
/dev/sda  /dev/sdc  /dev/sde   /dev/sde2  /dev/sdf  /dev/sdh
/dev/sdb  **/dev/sdd ** /dev/sde1  /dev/sde5  /dev/sdg

The sd card when inserted should show up as **/dev/sdd** but doesn't always, seems like it works at random.  

root@Starbug1:/dev/disk# cd by-id/
root@Starbug1:/dev/disk/by-id# ll
total 0
drwxr-xr-x 2 root root 400 Nov  3 13:09 ./
drwxr-xr-x 6 root root 120 Nov  3 13:09 ../
lrwxrwxrwx 1 root root   9 Nov  3 13:27 ata-HL-DT-ST_BD-RE_WH10LS30_K94A7NG3343 -> ../../sr0
lrwxrwxrwx 1 root root   9 Nov  3 13:27 ata-WDC_WD20EARS-22MVWB0_WD-WCAZA3932361 -> ../../sde
lrwxrwxrwx 1 root root  10 Nov  3 13:27 ata-WDC_WD20EARS-22MVWB0_WD-WCAZA3932361-part1 -> ../../sde1
lrwxrwxrwx 1 root root  10 Nov  3 13:27 ata-WDC_WD20EARS-22MVWB0_WD-WCAZA3932361-part2 -> ../../sde2
lrwxrwxrwx 1 root root  10 Nov  3 13:27 ata-WDC_WD20EARS-22MVWB0_WD-WCAZA3932361-part5 -> ../../sde5
lrwxrwxrwx 1 root root   9 Nov  3 13:27 md-name-RedDwarf:0 -> ../../md0
lrwxrwxrwx 1 root root   9 Nov  3 13:27 md-uuid-ce64cea7:a44326cf:6120e004:8a6e38a7 -> ../../md0
lrwxrwxrwx 1 root root   9 Nov  3 13:27 usb-Generic_USB_CF_Reader_18E3312D81B0-0:1 -> ../../sdb
lrwxrwxrwx 1 root root   9 Nov  3 13:27 usb-Generic_USB_MS_Reader_18E3312D81B0-0:3 -> ../../sdd
lrwxrwxrwx 1 root root   9 Nov  3 13:27 usb-Generic_USB_SD_Reader_18E3312D81B0-0:0 -> ../../sda
lrwxrwxrwx 1 root root   9 Nov  3 13:27 usb-Generic_USB_SM_Reader_18E3312D81B0-0:2 -> ../../sdc
lrwxrwxrwx 1 root root   9 Nov  3 13:27 usb-WDC_WD30_EFRX-68EUZN0_152D00539000-0:0 -> ../../sdf
lrwxrwxrwx 1 root root   9 Nov  3 13:27 usb-WDC_WD30_EFRX-68EUZN0_152D00539000-0:1 -> ../../sdg
lrwxrwxrwx 1 root root   9 Nov  3 13:27 usb-WDC_WD30_EFRX-68EUZN0_152D00539000-0:2 -> ../../sdh
lrwxrwxrwx 1 root root   9 Nov  3 13:27 wwn-0x50014ee2057e2751 -> ../../sde
lrwxrwxrwx 1 root root  10 Nov  3 13:27 wwn-0x50014ee2057e2751-part1 -> ../../sde1
lrwxrwxrwx 1 root root  10 Nov  3 13:27 wwn-0x50014ee2057e2751-part2 -> ../../sde2
lrwxrwxrwx 1 root root  10 Nov  3 13:27 wwn-0x50014ee2057e2751-part5 -> ../../sde5

root@Starbug1:/dev/disk/by-id# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.6M  1.6G   1% /run
/dev/sde1       1.8T   85G  1.7T   5% /
tmpfs           7.8G   40M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           7.8G  3.6M  7.8G   1% /tmp
tmpfs           1.6G   12K  1.6G   1% /run/user/121
tmpfs           1.6G   40K  1.6G   1% /run/user/1000

Any thoughts on what I can do here?

---

### Post by efflandt on 2017-11-05
Actually the built-in Fitipower card reader seems to work fine. The device that would not activate or show up (on that computer only)  was the "Genesys Logic, Inc. Logilink CR0012" external USB card reader,  and I was wondering if there was some conflict between it and the  Fitipower. The Genesys device worked fine on all other computers I tried  it on, even very old ones which may have been USB 1.0.

**cary-proust** are you sure that you are inserting your SD card in the correct slot? You highlight **/dev/sdd**, but your SD reader is **/dev/sda**:
lrwxrwxrwx 1 root root   9 Nov  3 13:27 usb-Generic_USB_**SD_Reader**_18E3312D81B0-0:0 -> ../../**sda**

Also make sure you do not have the card turned around which I just did when checking in dim light if my Fitipower SD card slot still worked fine.

---

