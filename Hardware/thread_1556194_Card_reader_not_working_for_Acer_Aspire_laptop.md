---
title: "Card reader not working for Acer Aspire laptop"
date: 2010-08-19
forum: Hardware
---

### Post by wanwarlock on 2010-08-19
Hi all

Recent convert to Ubuntu 10.04. All working well apart from email/chat which I have posted in the networking forum.

Anyway, just noticed that the card reader on my Acer Aspire 5102 laptop does not work or recognise my cards either sd or memory stick.

lspc:

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

it is all there but it can't read the cards. searching does not find any solutions in the forum.

any help?

thanks

---

### Post by wanwarlock on 2010-08-19
*bump.....

---

### Post by varunendra on 2010-08-21
Insert a card in the reader, then see if ```
sudo fdisk -l
``` can show it in the drives' list. If it does, then manual mounting is possible. If not, then maybe you need to update via update manager or see if there is a proprietary driver available under System>Administration>Hardware Drivers.

You said > ....does not work or recognise my cards either sd or memory [COLOR=Red]**stick**[/COLOR].
Do you mean it is unable to mount even a USB Flash Drive?

---

### Post by wanwarlock on 2010-08-21
> **varunendra said:**
> Insert a card in the reader, then see if ```
sudo fdisk -l
``` can show it in the drives' list. If it does, then manual mounting is possible. If not, then maybe you need to update via update manager or see if there is a proprietary driver available under System>Administration>Hardware Drivers.

You said 
Do you mean it is unable to mount even a USB Flash Drive?

Hi thanks for the reply.

fdisk:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1679

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris
```so it seems that it is not even recognising the sd card.

Memory stick is sony's 'memory stick' cards.

USB thumb drives work fine.

Wil try and update the drivers and see. 

Thanks again for the help

---

### Post by wanwarlock on 2010-08-21
I did try to update using the hardware drivers but it says no 'propriety drivers are in use in this system'

What do I do now??

---

### Post by varunendra on 2010-08-23
Sorry for not coming up with a solution, but a quick suggestion for now is to try a Live CD of some other distro like Mint9, Slax, etc. & see if the card gets detected there.

Also, does **dmesg** command show any errors about 'flash' or 'card reader'?

---

### Post by wanwarlock on 2010-08-25
> **varunendra said:**
> Sorry for not coming up with a solution, but a quick suggestion for now is to try a Live CD of some other distro like Mint9, Slax, etc. & see if the card gets detected there.

Also, does **dmesg** command show any errors about 'flash' or 'card reader'?

hi

haven't had a chance to dload any new live cds as yet, but dmesg did not give any errors, 

```
[   15.775673] sdhci: Secure Digital Host Controller Interface driver
[   15.775676] sdhci: Copyright(c) Pierre Ossman
[   15.785758] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[   15.785783]   alloc irq_desc for 23 on node -1
[   15.785785]   alloc kstat_irqs on node -1
[   15.785792] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   15.785961] Registered led device: mmc0::
[   15.786019] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
[   15.786039] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[   15.786055] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[   15.786061] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   15.786125] Registered led device: mmc1::
[   15.786180] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO

```

i'm sure there are others like me using an acer laptop??

any other help?

---

### Post by varunendra on 2010-08-25
> **wanwarlock said:**
> i'm sure there are others like me using an acer laptop??

....sure! Trying another OS has become just a routine check for me (especially with Lucid, since I've seen plenty of complains about its incompatibility with hardwares that were compatible with previous versions!) to ensure that the problem is not on the hardware side.

Another stupid question (stupid in the sense that the device is already detected & no errors reported, still I want to check this-):-
Have you crosschecked that the card reader is enabled in the BIOS?

If you can, please try [Slax]("http://www.slax.org/get_slax.php") just to check. It is only 200 MB download & can also be simply copied to a USB thumb drive making it bootable (see instructions in download).

---

### Post by avacado on 2010-10-14
try $ lsusb
if you have the 0cf2:6250 ENE technology then same card reader as me.

If so please subscribe to my bug and add weight to the problem.
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/633852]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852")

It may take some time for a volunteer developer to write the driver.
In the mean time use an external card reader or camera to read\write to card.

---

### Post by LandRacer on 2010-10-22
Well I can say I have a little older HP laptop. Seems the SD card reader works on boot. After the first suspend. It stops working.

So, there is some issue going on in this department.

lspci says;

> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0a:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
0a:00.4 System peripheral: JMicron Technology Corp. xD Host Controller


So all devices seem accounted for. It just doesn't work. See I can careless. But I figured I'd add my 2 cents. 

ITS BROKEN!

lsusb

> Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                                         
Bus 002 Device 004: ID 0930:a000 Toshiba Corp.                                                                                                         
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0408:03ba Quanta Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

All my usb devices work in any usb port. So. Maybe it is just crap Chinese hardware?

Well, here is what I can report for registered drives. This is with the SD chip in the reader.

sudo fdisk -l

> 
Disk /dev/sda: 32.0 GB, 32019111936 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00038679

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          65      522081   83  Linux
/dev/sda2            3371        3892     4192965   82  Linux swap / Solaris
/dev/sda3              66        3370    26547412+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 45.2 GB, 45171671040 bytes
255 heads, 63 sectors/track, 5491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d8a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3370    27069493+  83  Linux
/dev/sdb2            3371        5491    17036932+  83  Linux


Who needs a card reader anyhow. Those are for the birds.

I don't really need resolve. BUT avacado needs some backing. His reader needs some help.

---

### Post by piscator100 on 2011-02-22
Did anyone find a solution for this?  I have an Acer Aspire one and I have just changed ti unbuntu  and my card reader has stopped working - I am on 10.06 I believe?

---

