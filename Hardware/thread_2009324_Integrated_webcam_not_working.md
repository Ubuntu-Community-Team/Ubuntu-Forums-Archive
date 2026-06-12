---
title: "Integrated webcam not working"
date: 2012-06-24
forum: Hardware
---

### Post by ciniabitfarago on 2012-06-24
Hi,

I have an HP EliteBook 8460p. Previously I was runing a WIndows 7 but I decided to finish with it, so now is a Ubuntu 12.04 installed. Beside other peripherals the integrated webcam is missing, too. I installed the cheese but when I start it, complains the the device is missing. See the outputs of my first ideeas:

**lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse

**lspci **
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
23:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
23:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
23:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
24:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)
25:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

**ls /dev/video0**
ls: cannot access /dev/video0: No such file or directory

Any suggestion?

Abitfarago Cini

---

### Post by gordintoronto on 2012-06-24
According to this page:
[http://www.linlap.com/wiki/hp+elitebook+8460p](http://www.linlap.com/wiki/hp+elitebook+8460p) 

the webcam should work. What do you get from these commands:
uname -a
ls /dev

The 8460p is a large family of computers, perhaps you could describe yours?

Did the webcam work in Windows? I've seen computers where the cable from the webcam wasn't actually plugged in.

---

### Post by graflaszlo on 2012-06-28
Hi,

**uname -a**
```
Linux saratoga 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
```**ls /dev**
```
agpgart          fw0           net                 ram4      stdin   tty24  tty43  tty62      ttyS22   usbmon2
autofs           hidraw0       network_latency     ram5      stdout  tty25  tty44  tty63      ttyS23   usbmon3
block            hpet          network_throughput  ram6      tpm0    tty26  tty45  tty7       ttyS24   usbmon4
bsg              input         null                ram7      tty     tty27  tty46  tty8       ttyS25   vcs
btrfs-control    kmsg          oldmem              ram8      tty0    tty28  tty47  tty9       ttyS26   vcs1
bus              log           parport0            ram9      tty1    tty29  tty48  ttyprintk  ttyS27   vcs2
cdrom            loop0         port                random    tty10   tty3   tty49  ttyS0      ttyS28   vcs3
char             loop1         ppp                 rfkill    tty11   tty30  tty5   ttyS1      ttyS29   vcs4
console          loop2         psaux               rtc       tty12   tty31  tty50  ttyS10     ttyS3    vcs5
core             loop3         ptmx                rtc0      tty13   tty32  tty51  ttyS11     ttyS30   vcs6
cpu              loop4         pts                 sda       tty14   tty33  tty52  ttyS12     ttyS31   vcsa
cpu_dma_latency  loop5         ram0                sda1      tty15   tty34  tty53  ttyS13     ttyS4    vcsa1
disk             loop6         ram1                sda2      tty16   tty35  tty54  ttyS14     ttyS5    vcsa2
dri              loop7         ram10               sda5      tty17   tty36  tty55  ttyS15     ttyS6    vcsa3
dvd              loop-control  ram11               sg0       tty18   tty37  tty56  ttyS16     ttyS7    vcsa4
ecryptfs         lp0           ram12               sg1       tty19   tty38  tty57  ttyS17     ttyS8    vcsa5
fb0              mapper        ram13               shm       tty2    tty39  tty58  ttyS18     ttyS9    vcsa6
fd               mcelog        ram14               snapshot  tty20   tty4   tty59  ttyS19     uinput   vga_arbiter
freefall         mei           ram15               snd       tty21   tty40  tty6   ttyS2      urandom  watchdog
full             mem           ram2                sr0       tty22   tty41  tty60  ttyS20     usbmon0  zero
fuse             mmcblk0       ram3                stderr    tty23   tty42  tty61  ttyS21     usbmon1

```Are they useful?

---

### Post by gordintoronto on 2012-06-29
The partial list is not helpful.

Did the webcam ever work?

---

### Post by ciniabitfarago on 2012-06-30
Hi,

the last reply is not relevant for me, probably a cross-posting. But thanks for his/her help.

Yes, the webcam was working well with Windows 7, but there is no video device present on my machine (Ubuntu 12.04 LTS, 3.2.0-26-generic-pae)

Abitfarago Cini

---

### Post by asimali on 2012-07-01
my webcam is working with cheese not working in empathy messenger. 
the web cam is also not shown in lsusb.
this is the result of lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 1bcf:2888 Sunplus Innovation Technology Inc. 
Bus 002 Device 004: ID 148f:2000 Ralink Technology, Corp. 
Bus 002 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E169/E620/E800 HSDPA Modem

please help

---

### Post by lanpangzhu on 2012-07-02
my webcam was working on LTS 12.04 until last week some time. 

Linux austin 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 athlon i386 GNU/Linux

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 138a:0018 Validity Sensors, Inc. 
Bus 003 Device 002: ID 0a5c:21e3 Broadcom Corp. 


00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Mobility Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
03:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

---

