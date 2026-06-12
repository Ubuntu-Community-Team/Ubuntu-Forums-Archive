---
title: "Trouble mounting SD Card (7.10)"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by taser on 2007-10-28
I'm having a heck of a time trying to mount an SD card on my laptop running Ubuntu 7.10. The SD card is actually an adapter for a microSDHC card, but I don't think it makes a difference. It would mount flawlessly on Feisty Fawn (7.04) but Gutsy Gibbon is being mule-headed.

The moment I try to mount it, Nautilus pops up something like this:
mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0p1, 
missong codepage or helper program or other error
In some cases useful info is found in syslog -try
dmesg | tail or so

- - - -

dmesg | tail:
[121066.732000] tifm_core: MMC/SD card detected in socket 0:3
[121067.740000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[121067.744000]  mmcblk0: p1
[121068.232000] FAT: Unrecognized mount option "usefree" or missing value
[121569.312000] tifm0 : demand removing card from socket 0:3
[121578.248000] tifm_core: MMC/SD card detected in socket 0:3
[121579.148000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[121579.152000]  mmcblk0: p1
[121579.468000] FAT: Unrecognized mount option "usefree" or missing value
[122168.824000] FAT: Unrecognized mount option "usefree" or missing value

- - - -

From dmesg | grep SD:
[    0.000000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f69d0
[    0.000000] ACPI: RSDT (v001 TOSCPL   RSDT   0x06040000  LTP 0x00000000) @ 0x5f6e21a0
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20030224) @ 0x5f6e30b6
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20030224) @ 0x5f6e2a24
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x5f6e25df
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x5f6e2401
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x5f6e21e8
[    0.000000] ACPI: DSDT (v001 TOSCPL ALVISO   0x06040000 MSFT 0x0100000e) @ 0x00000000
[   22.697711] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   26.052000] sdhci: SDHCI controller found at 0000:06:04.4 [104c:8034] (rev 0)
[   26.052000] mmc0: SDHCI at 0xb8009000 irq 20 DMA
[   26.056000] mmc1: SDHCI at 0xb8008c00 irq 20 DMA
[   26.056000] mmc2: SDHCI at 0xb8008800 irq 20 DMA
[116208.036000] tifm_core: MMC/SD card detected in socket 0:3
[116208.856000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[116234.548000] tifm_core: MMC/SD card detected in socket 0:3
[116264.348000] tifm_core: MMC/SD card detected in socket 0:3
[116265.320000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[116731.196000] tifm_core: MMC/SD card detected in socket 0:3
[116732.156000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[116765.760000] tifm_core: MMC/SD card detected in socket 0:3
[116766.608000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[117246.876000] tifm_core: MMC/SD card detected in socket 0:3
[117636.856000] tifm_core: MMC/SD card detected in socket 0:3
[117637.684000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[117699.160000] tifm_core: MMC/SD card detected in socket 0:3
[118036.312000] tifm_core: MMC/SD card detected in socket 0:3
[118302.940000] tifm_core: MMC/SD card detected in socket 0:3
[118390.112000] tifm_core: MMC/SD card detected in socket 0:3
[118884.516000] tifm_core: MMC/SD card detected in socket 0:3
[118952.172000] tifm_core: MMC/SD card detected in socket 0:3
[118991.112000] tifm_core: MMC/SD card detected in socket 0:3
[120166.316000] tifm_core: MMC/SD card detected in socket 0:3
[121066.732000] tifm_core: MMC/SD card detected in socket 0:3
[121067.740000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[121578.248000] tifm_core: MMC/SD card detected in socket 0:3
[121579.148000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 

- - - -

 dmesg | grep SD
[    0.000000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f69d0
[    0.000000] ACPI: RSDT (v001 TOSCPL   RSDT   0x06040000  LTP 0x00000000) @ 0x5f6e21a0
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20030224) @ 0x5f6e30b6
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20030224) @ 0x5f6e2a24
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x5f6e25df
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x5f6e2401
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x5f6e21e8
[    0.000000] ACPI: DSDT (v001 TOSCPL ALVISO   0x06040000 MSFT 0x0100000e) @ 0x00000000
[   22.697711] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   26.052000] sdhci: SDHCI controller found at 0000:06:04.4 [104c:8034] (rev 0)
[   26.052000] mmc0: SDHCI at 0xb8009000 irq 20 DMA
[   26.056000] mmc1: SDHCI at 0xb8008c00 irq 20 DMA
[   26.056000] mmc2: SDHCI at 0xb8008800 irq 20 DMA
[116208.036000] tifm_core: MMC/SD card detected in socket 0:3
[116208.856000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[116234.548000] tifm_core: MMC/SD card detected in socket 0:3
[116264.348000] tifm_core: MMC/SD card detected in socket 0:3
[116265.320000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[116731.196000] tifm_core: MMC/SD card detected in socket 0:3
[116732.156000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[116765.760000] tifm_core: MMC/SD card detected in socket 0:3
[116766.608000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[117246.876000] tifm_core: MMC/SD card detected in socket 0:3
[117636.856000] tifm_core: MMC/SD card detected in socket 0:3
[117637.684000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[117699.160000] tifm_core: MMC/SD card detected in socket 0:3
[118036.312000] tifm_core: MMC/SD card detected in socket 0:3
[118302.940000] tifm_core: MMC/SD card detected in socket 0:3
[118390.112000] tifm_core: MMC/SD card detected in socket 0:3
[118884.516000] tifm_core: MMC/SD card detected in socket 0:3
[118952.172000] tifm_core: MMC/SD card detected in socket 0:3
[118991.112000] tifm_core: MMC/SD card detected in socket 0:3
[120166.316000] tifm_core: MMC/SD card detected in socket 0:3
[121066.732000] tifm_core: MMC/SD card detected in socket 0:3
[121067.740000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 
[121578.248000] tifm_core: MMC/SD card detected in socket 0:3
[121579.148000] mmcblk0: mmc3:cde2 SD01G 1006080KiB 

- - - -

From lspci:
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

---

### Post by kspn on 2007-10-30
Any one have a fix for this under Xubuntu?

---

### Post by gene6482 on 2007-11-02
I'm having the same issue here.

---

### Post by ljonesj on 2007-11-02
every so often i have that problem with my cards try reformating it

---

### Post by jmomandia on 2007-11-03
I also got this when trying to mount my USB in 7.10, a problem I didn't encounter in Feisty.

[17179671.092000] sdb: Mode Sense: 03 00 00 00
[17179671.092000] sdb: assuming drive cache: write through
[17179671.092000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
[17179671.092000] sdb: Write Protect is off
[17179671.092000] sdb: Mode Sense: 03 00 00 00
[17179671.092000] sdb: assuming drive cache: write through
[17179671.092000]  sdb: sdb1
[17179671.096000] sd 3:0:0:0: Attached scsi removable disk sdb
[17179671.096000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[17179671.356000] FAT: Unrecognized mount option "usefree" or missing value

---

### Post by jmomandia on 2007-11-03
I don't know if this helps, but for my USB drive, the solution to Bug #151025 worked.
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

HERE'S THE FIX:
--------------------

Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)

So I did APPLICATIONS --> SYSTEM TOOLS --> CONFIGURATION EDITOR --> opened SYSTEM --> STORAGE --> DEFAULT OPTIONS --> right-clicked on MOUNT OPTIONS --> EDIT KEY --> removed USEFREE option from the list.

Thanks to Dan Lenski.

---

### Post by kspn on 2007-11-04
Tried that, Didn't work for me under Xubuntu.

---

### Post by gene6482 on 2007-11-04
Thanks a bunch.  FIxed it for me.
> **jmomandia said:**
> I don't know if this helps, but for my USB drive, the solution to Bug #151025 worked.
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

HERE'S THE FIX:
--------------------

Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)

So I did APPLICATIONS --> SYSTEM TOOLS --> CONFIGURATION EDITOR --> opened SYSTEM --> STORAGE --> DEFAULT OPTIONS --> right-clicked on MOUNT OPTIONS --> EDIT KEY --> removed USEFREE option from the list.

Thanks to Dan Lenski.

---

### Post by Kizik on 2007-11-04
> **jmomandia said:**
> I don't know if this helps, but for my USB drive, the solution to Bug #151025 worked.
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

HERE'S THE FIX:
--------------------

Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)

So I did APPLICATIONS --> SYSTEM TOOLS --> CONFIGURATION EDITOR --> opened SYSTEM --> STORAGE --> DEFAULT OPTIONS --> right-clicked on MOUNT OPTIONS --> EDIT KEY --> removed USEFREE option from the list.

Thanks to Dan Lenski.

This worked for me as well.  Of course, I started wondering what "[FONT="System"]usefree[/FONT]" was there for and what have I now broken.  :confused:

Here is the info on why "usefree" is there: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567/comments/53]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567/comments/53")

So, I look forward to 8.04 for the "correct" fix and will stick with the above hack for now.

---

### Post by LauraSakura on 2007-11-13
thank you so much! ever since I updated to gutsy I could not get my iPod or USB Stick to mount and now after removing "usefree" they mount fine. Thanks so much!!!

---

### Post by Endolith on 2008-05-02
> **Kizik said:**
> Here is the info on why "usefree" is there: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567/comments/53]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567/comments/53")

So, I look forward to 8.04 for the "correct" fix and will stick with the above hack for now.

This does not appear to have been fixed in 8.04.  The "usefree" option is still there.

---

