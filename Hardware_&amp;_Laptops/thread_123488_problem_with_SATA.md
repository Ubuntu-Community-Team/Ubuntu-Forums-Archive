---
title: "problem with SATA"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by shm on 2006-01-30
I have ubuntu breezy, kernel image 2.6.12-9-386 (just install, no other programs! (mc only :) ) )
When i'm copy 600Mb from one folder to another mc show speed about 2Mb/sec
When i'm booting from Ubuntu Install cd, switch in to console 2 (alt+F2)
#mkdir /mnt
#mount /dev/sda1 /mnt
#chroot /mnt
#mc
Then when i copy 600Mb, mc show speed about 40Mb/sec!!!
Kernel image on Install CD and on my hard drive  the same!
What is wrong?


I'm unpack /cdrom/install/initrd.gz 
then mount it
#mount ./initrd /root/tmp -o loop
and repack
#find * | cpio -o -H newc | gzip -9 -c > ../initrd.img-`uname -r`.new
#cp ./initrd.img-`uname -r`.new /boot/initrd.img-`uname -r`
#reboot
Then speed also good but init scripts didn't work :( 
I'm also try oher SATA controller, but it did'n resolve problem.
(In my motherboard ICH5 (sata_piix) sata controller now i'm use VIA sata controller (sata_via))


Please HELP ME! :)


Sorry for my English i'm from Russia.

Some useful info:
root@denis:/root/tmp# lsmod
Module                  Size  Used by
isofs                  32824  1
udf                    75524  0
i915                   17920  1
drm                    58004  2 i915
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm                78344  2 snd_intel8x0,snd_ac97_codec
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
hw_random               5268  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
nls_utf8                2176  1
nls_cp437               5888  2
vfat                   12288  1
fat                    46492  1 vfat
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
lp                     11460  0
parport                32072  1 lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  5
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
sata_via                8836  8
libata                 47876  1 sata_via
scsi_mod              124872  2 sd_mod,libata
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  3 ehci_hcd,uhci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_generic             1664  0
piix                    9476  1
ide_core              125268  3 ide_cd,ide_generic,piix
unix                   24624  706
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon



root@denis:/root/tmp# lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82865G Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:0a.0 RAID bus controller: VIA Technologies, Inc.: Unknown device 3249 (rev 50)
0000:01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



root@denis:/root/tmp# dmesg
.....
[4294672.043000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.043000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.043000] ACPI: bus type ide registered
[4294672.049000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294672.049000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294672.049000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294672.049000] ICH5: chipset revision 2
[4294672.049000] ICH5: not 100% native mode: will probe irqs later
[4294672.049000] ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[4294672.049000] ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:DMA
[4294672.049000] Probing IDE interface ide0...
[4294672.568000] Probing IDE interface ide1...
[4294673.494000] hdd: _NEC DVD_RW ND-3500AG, ATAPI CD/DVD-ROM drive
[4294673.545000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.545000] Probing IDE interface ide0...
[4294674.064000] Probing IDE interface ide2...
[4294674.576000] Probing IDE interface ide3...
[4294675.088000] Probing IDE interface ide4...
[4294675.600000] Probing IDE interface ide5...
[4294676.117000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294676.117000] Uniform CD-ROM driver Revision: 3.20
[4294676.529000] usbcore: registered new driver usbfs
[4294676.529000] usbcore: registered new driver hub
[4294676.530000] USB Universal Host Controller Interface driver v2.2
[4294676.530000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294676.530000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294676.530000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
[4294676.592000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294676.592000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eec0
[4294676.592000] hub 1-0:1.0: USB hub found
[4294676.592000] hub 1-0:1.0: 2 ports detected
[4294676.595000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294676.595000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294676.595000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
[4294676.657000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294676.657000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ef00
[4294676.657000] hub 2-0:1.0: USB hub found
[4294676.657000] hub 2-0:1.0: 2 ports detected
[4294676.660000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294676.660000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294676.660000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI #3
[4294676.722000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294676.722000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef20
[4294676.722000] hub 3-0:1.0: USB hub found
[4294676.722000] hub 3-0:1.0: 2 ports detected
[4294676.725000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[4294676.725000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294676.725000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
[4294676.761000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294676.787000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294676.787000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef40
[4294676.787000] hub 4-0:1.0: USB hub found
[4294676.787000] hub 4-0:1.0: 2 ports detected
[4294676.822000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[4294676.822000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294676.822000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
[4294676.822000] ehci_hcd 0000:00:1d.7: debug port 1
[4294676.822000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294676.822000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe77b800
[4294676.826000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294676.826000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.826000] hub 5-0:1.0: USB hub found
[4294676.826000] hub 5-0:1.0: 8 ports detected
[4294676.896000] SCSI subsystem initialized
[4294676.897000] libata version 1.11 loaded.
[4294676.898000] sata_via version 1.1
[4294676.898000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294676.898000] PCI: Via IRQ fixup for 0000:01:0a.0, from 10 to 5
[4294676.898000] sata_via(0000:01:0a.0): routed to hard irq line 5
[4294676.898000] ata1: SATA max UDMA/133 cmd 0xDFA0 ctl 0xDFAA bmdma 0xDF40 irq 21
[4294676.899000] ata2: SATA max UDMA/133 cmd 0xDF90 ctl 0xDF9A bmdma 0xDF48 irq 21
[4294677.103000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:007f
[4294677.103000] ata1: dev 0 ATA, max UDMA/133, 156299375 sectors: lba48
[4294677.103000] ata1: dev 0 configured for UDMA/133
[4294677.103000] scsi0 : sata_via
[4294677.235000] usb 1-1: device not accepting address 2, error -71
[4294677.304000] ata2: no device found (phy stat 00000000)
[4294677.304000] scsi1 : sata_via
[4294677.304000] Vendor: ATA Model: ST380817AS Rev: 3.42
[4294677.304000] Type: Direct-Access ANSI SCSI revision: 05
[4294677.315000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294677.315000] 8139cp: pci dev 0000:01:0d.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294677.315000] 8139cp: Try the "8139too" driver instead.
[4294677.317000] 8139too Fast Ethernet driver 0.9.27
[4294677.317000] ACPI: PCI Interrupt 0000:01:0d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294677.317000] eth0: RealTek RTL8139 at 0xd400, 00:13:d4:08:2b:40, IRQ 23
[4294677.317000] eth0: Identified 8139 chip type 'RTL-8101'
[4294677.761000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4294679.376000] SCSI device sda: 156299375 512-byte hdwr sectors (80025 MB)
[4294679.376000] SCSI device sda: drive cache: write back
[4294679.376000] SCSI device sda: 156299375 512-byte hdwr sectors (80025 MB)
[4294679.376000] SCSI device sda: drive cache: write back
[4294679.376000] /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4
[4294679.406000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
.....

---

