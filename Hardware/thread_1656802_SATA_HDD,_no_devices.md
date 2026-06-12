---
title: "SATA HDD, no devices?"
date: 2010-12-31
forum: Hardware
---

### Post by DocShaman on 2010-12-31
Overview:

Lets see if I can get this right...way too rusty on this stuff

I am having an issue with Ubuntu 10.10 not showing my SATA HDDs. Think its not creating the devices.
The drives sometimes but rarely show under live CD boot. 

-The problem happens from disk image or from Live CD. 
-When booting from disk, it finds /boot on partition 2 and loads the image, but then won't load root on the same drive partition 6
-I am dual boot w/ Windows on the same physical SATA drive but in different partitions.
  Windows works flawlessly. So, I don't _think_ its a hardware problem but perhaps a kernel param loading issue? 
-sata is enabled in bios
-sata raid is disabled in bios
-boot/root drive is /dev/sda1 when found
-/dev/sda2 not formatted(?)

Any Thoughts how to troubleshoot further? 

Thanks


Details:  # from liveCD boot

**ubuntu@ubuntu:~$ uname -a**
Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

**ubuntu@ubuntu:~$ cat /proc/cmdline**
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity


**ubuntu@ubuntu:/proc$ sudo blkid**
/dev/loop0: TYPE="squashfs" 


**ubuntu@ubuntu:~$ more /proc/scsi/scsi**
Attached devices:
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ASUS     Model: DRW-2014L1T      Rev: 1.00
  Type:   CD-ROM                           ANSI  SCSI revision: 05

**ubuntu@ubuntu:~$ dmesg | grep -i ata**
[    0.000000]  BIOS-e820: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]  modified: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000] Memory: 8178632k/9699328k available (5708k kernel code, 1312276k absent, 208420k reserved, 5382k data, 908k init)
[    0.017867] PEBS disabled due to CPU errata.
[    0.856592] libata version 3.00 loaded.
[    3.520874] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    3.521270] pata_acpi 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 23 (level, low) -> IRQ 23
[    3.521301] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    3.521310] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    3.521669] pata_acpi 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 22 (level, low) -> IRQ 22
[    3.521700] pata_acpi 0000:00:0e.1: setting latency timer to 64
[    3.521710] pata_acpi 0000:00:0e.1: PCI INT B disabled
[    3.522062] pata_acpi 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    3.522091] pata_acpi 0000:00:0e.2: setting latency timer to 64
[    3.522101] pata_acpi 0000:00:0e.2: PCI INT C disabled
[    3.597991] Write protecting the kernel read-only data: 10240k
[    3.655635] pata_amd 0000:00:0d.0: version 0.4.1
[    3.655693] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.675207] scsi0 : pata_amd
[    3.682709] scsi1 : pata_amd
[    3.683574] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    3.683577] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    3.683650] sata_nv 0000:00:0e.0: version 3.5
[    3.683669] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 23 (level, low) -> IRQ 23
[    3.683674] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.684031] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.692460] scsi2 : sata_nv
[    3.696748] scsi3 : sata_nv
[    3.697031] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    3.697035] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    3.697082] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 22 (level, low) -> IRQ 22
[    3.697085] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    3.697160] sata_nv 0000:00:0e.1: setting latency timer to 64
[    3.704417] scsi4 : sata_nv
[    3.704574] scsi5 : sata_nv
[    3.704796] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[    3.704799] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[    3.704834] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    3.704837] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    3.704894] sata_nv 0000:00:0e.2: setting latency timer to 64
[    3.705011] scsi6 : sata_nv
[    3.705078] scsi7 : sata_nv
[    3.705271] ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    3.705275] ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    3.851233] ata2: port disabled. ignoring.
[    4.030130] ata7: SATA link down (SStatus 0 SControl 300)
[    4.190034] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.210159] ata5.00: ATAPI: ASUS    DRW-2014L1T, 1.00, max UDMA/66
[    4.251428] ata5.00: configured for UDMA/66
[    9.230014] ata3: link is slow to respond, please be patient (ready=0)
[   13.730017] ata3: SRST failed (errno=-16)
[   19.260015] ata3: link is slow to respond, please be patient (ready=0)
[   23.760018] ata3: SRST failed (errno=-16)
[   29.290016] ata3: link is slow to respond, please be patient (ready=0)
[   58.810012] ata3: SRST failed (errno=-16)
[   58.810017] ata3: limiting SATA link speed to 1.5 Gbps
[   63.860011] ata3: SRST failed (errno=-16)
[   63.860014] ata3: reset failed, giving up
[   69.390016] ata4: link is slow to respond, please be patient (ready=0)
[   73.890018] ata4: SRST failed (errno=-16)
[   79.420017] ata4: link is slow to respond, please be patient (ready=0)
[   83.920013] ata4: SRST failed (errno=-16)
[   89.450018] ata4: link is slow to respond, please be patient (ready=0)
[  118.970020] ata4: SRST failed (errno=-16)
[  118.970025] ata4: limiting SATA link speed to 1.5 Gbps
[  124.021276] ata4: SRST failed (errno=-16)
[  124.021279] ata4: reset failed, giving up
[  124.350020] ata6: SATA link down (SStatus 0 SControl 300)
[  124.680020] ata8: SATA link down (SStatus 0 SControl 300)


**ubuntu@ubuntu:~$ ls /dev/sd* /dev/hd* /dev/sg***
ls: cannot access /dev/sd*: No such file or directory
ls: cannot access /dev/hd*: No such file or directory
/dev/sg0

**ubuntu@ubuntu:/proc$ sudo lspci**
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for mainboards (rev a2)
02:00.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for mainboards (rev a2)
02:02.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for mainboards (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

**ubuntu@ubuntu:~$ egrep -i '(err|warn|excep)' /var/log/messages**
Dec 31 08:34:08 ubuntu kernel: [    0.017867] PEBS disabled due to CPU errata.
Dec 31 08:34:08 ubuntu kernel: [    0.716365] ACPI: Using IOAPIC for interrupt routing
Dec 31 08:34:08 ubuntu kernel: [    0.849393] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.849561] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.849725] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.849891] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.850078] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.850241] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.850404] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.850567] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.850732] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.850900] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.851064] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.851234] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.851396] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.851560] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.851722] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.851887] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.852050] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.852219] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
Dec 31 08:34:08 ubuntu kernel: [    0.852432] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.852635] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.852836] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.853038] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Dec 31 08:34:08 ubuntu kernel: [    0.853239] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
Dec 31 08:34:08 ubuntu kernel: [    0.853440] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.853640] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.853841] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.854042] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
Dec 31 08:34:08 ubuntu kernel: [    0.854244] ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0
Dec 31 08:34:08 ubuntu kernel: [    0.854446] ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0
Dec 31 08:34:08 ubuntu kernel: [    0.854648] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Dec 31 08:34:08 ubuntu kernel: [    0.854849] ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.855052] ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.855256] ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.855460] ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0
Dec 31 08:34:08 ubuntu kernel: [    0.855665] ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.
Dec 31 08:34:08 ubuntu kernel: [    0.855874] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0
Dec 31 08:34:08 ubuntu kernel: [    0.856077] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0
Dec 31 08:34:08 ubuntu kernel: [    0.856279] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
Dec 31 08:34:08 ubuntu kernel: [    3.521254] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 23
Dec 31 08:34:08 ubuntu kernel: [    3.521656] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 22
Dec 31 08:34:08 ubuntu kernel: [    3.522051] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
Dec 31 08:34:08 ubuntu kernel: [    3.522928] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 20
Dec 31 08:34:08 ubuntu kernel: [    3.540599] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
Dec 31 08:34:08 ubuntu kernel: [    3.685969] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Dec 31 08:34:08 ubuntu kernel: [    3.705668] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 22
Dec 31 08:34:08 ubuntu kernel: [    4.231088] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 21
Dec 31 08:34:08 ubuntu kernel: [  124.732950] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
Dec 31 08:34:16 ubuntu kernel: [  180.400054] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20

**ubuntu@ubuntu:/proc$ cat /proc/modules **
binfmt_misc 7984 1 - Live 0xffffffffa02e8000
parport_pc 30086 0 - Live 0xffffffffa0379000
ppdev 6804 0 - Live 0xffffffffa02da000
lp 10201 0 - Live 0xffffffffa005c000
dm_crypt 13381 0 - Live 0xffffffffa02b9000
parport 37032 3 parport_pc,ppdev,lp, Live 0xffffffffa036d000
snd_hda_codec_realtek 299533 1 - Live 0xffffffffa0321000
snd_hda_intel 26019 2 - Live 0xffffffffa0313000
snd_hda_codec 100919 2 snd_hda_codec_realtek,snd_hda_intel, Live 0xffffffffa02ec000
snd_hwdep 6660 1 snd_hda_codec, Live 0xffffffffa02e4000
snd_pcm 89104 2 snd_hda_intel,snd_hda_codec, Live 0xffffffffa02c2000
snd_seq_midi 5932 0 - Live 0xffffffffa02be000
snd_rawmidi 22207 1 snd_seq_midi, Live 0xffffffffa02b1000
snd_seq_midi_event 7291 1 snd_seq_midi, Live 0xffffffffa026d000
snd_seq 57512 2 snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa029c000
snd_timer 23850 2 snd_pcm,snd_seq, Live 0xffffffffa00db000
snd_seq_device 6912 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa0028000
snd 64117 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa028a000
psmouse 62080 0 - Live 0xffffffffa0270000
serio_raw 4910 0 - Live 0xffffffffa0269000
i2c_nforce2 6155 0 - Live 0xffffffffa0096000
shpchp 34910 0 - Live 0xffffffffa00d0000
soundcore 1240 1 snd, Live 0xffffffffa002c000
snd_page_alloc 8588 2 snd_hda_intel,snd_pcm, Live 0xffffffffa0011000
squashfs 27681 1 - Live 0xffffffffa0107000
aufs 179029 4327 - Live 0xffffffffa023b000
nls_cp437 6375 1 - Live 0xffffffffa00ee000
isofs 34218 1 - Live 0xffffffffa0230000
dm_raid45 75026 0 - Live 0xffffffffa021b000
xor 4709 1 dm_raid45, Live 0xffffffffa002e000
btrfs 506518 0 - Live 0xffffffffa019d000
zlib_deflate 21866 1 btrfs, Live 0xffffffffa004c000
crc32c 3007 1 - Live 0xffffffffa0025000
libcrc32c 1268 1 btrfs, Live 0xffffffffa0005000
nouveau 568848 2 - Live 0xffffffffa0110000
ttm 68212 1 nouveau, Live 0xffffffffa00f4000
drm_kms_helper 32836 1 nouveau, Live 0xffffffffa00e3000
drm 206161 4 nouveau,ttm,drm_kms_helper, Live 0xffffffffa009b000
usbhid 42062 0 - Live 0xffffffffa0089000
hid 84678 1 usbhid, Live 0xffffffffa0072000
i2c_algo_bit 6208 1 nouveau, Live 0xffffffffa0031000
floppy 65299 0 - Live 0xffffffffa0060000
firewire_ohci 24679 0 - Live 0xffffffffa0053000
firewire_core 54327 1 firewire_ohci, Live 0xffffffffa003c000
forcedeth 55649 0 - Live 0xffffffffa0015000
crc_itu_t 1739 1 firewire_core, Live 0xffffffffa0036000
[B]sata_nv 23770 1 - Live 0xffffffffa0009000
pata_amd 12050 0 - Live 0xffffffffa0000000[/B]

---

### Post by oldfred on 2010-12-31
BIOS settings can make a difference. Also did you have RAID turned on at any point? That may leave settings on hard drive that interfere with Ubuntu.

I had to tweak some BIOS settings with a new motherboard and then started saving a list from others. See if any of these apply:

Some issues on booting install:
BIOS settings need USB mouse & keyboard
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
BIOS should be set for IDE compatibility mode
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

Bad write on CD - check md5sum, write at slowest speed, Use USB to install
CD or USB not written as bootable, just copied, DVD or RW (not just R only) sometimes an issue
Flexnet in Boot area (DRM "rights"/security)

---

### Post by DocShaman on 2010-12-31
Thanks for the reply.

I believe the chkdsk in windows was the kicker.

First I disabled my IDE HDD's in the bios. No Change.
Booted in to windows to try the easy chkdsk (Drve Properties, error checking), this asked if it could check the disk on reboot. I did check all the options, test for bad sectors and such). But before I rebooted I loaded new Nvidia Motherboard drivers for Windows XP (Doubt that did anything for MBR but who knows). 
Rebooted.
chkdsk did its thing.
Rebooted in to Ubuntu 8.04 this time. Worked fine.(saw the drivesin places and could mounted them). 
Rebooted in to Ubunto 10.10, again worked fine.
Rebooted in to /dev/SDA, has worked fine since. 

I am fairly certain that the chkdsk was the answer.

Thanks for the help

---

### Post by oldfred on 2010-12-31
Glad that worked.

I did not even notice it was in the list of things I had posted but I have had the same issue where one of my drives could not be seen by gparted until I ran chkdsk, even though my XP ran just fine.

---

