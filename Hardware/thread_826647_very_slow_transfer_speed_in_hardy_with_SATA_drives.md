---
title: "very slow transfer speed in hardy with SATA drives"
date: 2008-06-12
forum: Hardware
---

### Post by deepclutch on 2008-06-12
Hello,
 with latest hardy,when I tried copying a 10GB directory ,it took around **35minutes** to complete!:( 
hdparm for both SATA drives showed dma is activated.what will be the problem?I am on a 915GV based mobo with 2 seagate sata hdds.

lspci:
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```here is lsmod :
```
Module                  Size  Used by
xt_TCPMSS               4160  1 
xt_tcpmss               2240  1 
iptable_mangle          2944  1 
pppoe                   8896  2 
pppox                   3532  1 pppoe
ppp_generic            20316  6 pppoe,pppox
slhc                    5504  1 ppp_generic
binfmt_misc             7816  1 
ipv6                  234108  18 
video                  16464  0 
output                  3136  1 video
eee                     4968  0 
container               3712  0 
fuj02b1_acpi            5572  0 
sbs                    11336  0 
sbshc                   5440  1 sbs
wmi                     6632  0 
ac                      4420  0 
asus_acpi               6880  0 
battery                10308  0 
ipt_REJECT              3008  2 
xt_tcpudp               3072  5 
iptable_filter          2880  1 
ip_tables              10448  2 iptable_mangle,iptable_filter
x_tables               13828  5 xt_TCPMSS,xt_tcpmss,ipt_REJECT,xt_tcpudp,ip_tables
microcode               8688  0 
firmware_class          7232  1 microcode
fuse                   44444  3 
gspca                 609380  0 
videodev               28480  1 gspca
v4l1_compat            12484  1 videodev
it87                   17936  0 
hwmon_vid               2944  1 it87
snd_intel8x0           26076  3 
snd_pcsp                8800  1 
snd_ac97_codec         87524  1 snd_intel8x0
ac97_bus                1984  1 snd_ac97_codec
snd_pcm_oss            33056  0 
snd_pcm                62340  4 snd_intel8x0,snd_pcsp,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          12736  1 snd_pcm_oss
snd_seq_dummy           2948  0 
snd_seq_midi            6048  0 
snd_rawmidi            18784  1 snd_seq_midi
snd_seq_oss            25372  0 
snd_seq_midi_event      6656  2 snd_seq_midi,snd_seq_oss
snd_seq                41704  6 snd_seq_dummy,snd_seq_midi,snd_seq_oss,snd_seq_midi_event
snd_timer              18184  2 snd_pcm,snd_seq
snd_seq_device          6668  5 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq_oss,snd_seq
i2c_i801                8016  1 
iTCO_wdt                9636  0 
hci_usb                12444  0 
button                  6288  0 
psmouse                32144  0 
parport_pc             22228  0 
i2c_core               20052  2 eee,i2c_i801
evdev                   8256  3 
snd                    45816  19 snd_intel8x0,snd_pcsp,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_rawmidi,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
bluetooth              45476  1 hci_usb
parport                31380  1 parport_pc
serio_raw               4996  0 
soundcore               6856  1 snd
agpgart                29044  0 
rng_core                4164  0 
snd_page_alloc          8008  2 snd_intel8x0,snd_pcm
ext3                  105608  3 
jbd                    42388  1 ext3
mbcache                 7428  1 ext3
ide_cd_mod             27652  0 
cdrom                  30680  1 ide_cd_mod
sd_mod                 22168  6 
ata_generic             4868  0 
ata_piix               15300  6 
libata                139688  2 ata_generic,ata_piix
piix                    6792  0 [permanent]
8139cp                 16896  0 
scsi_mod              130748  2 sd_mod,libata
dock                    8528  1 libata
8139too                20352  0 
mii                     5184  2 8139cp,8139too
uhci_hcd               18832  0 
ide_pci_generic         4164  0 [permanent]
ehci_hcd               28108  0 
ide_core               92696  3 ide_cd_mod,piix,ide_pci_generic
usbcore               116624  5 gspca,hci_usb,uhci_hcd,ehci_hcd
thermal                15196  0 
processor              33456  1 thermal
fan                     4420  0 
```

---

### Post by prshah on 2008-06-12
> **deepclutch said:**
> tried copying a 10GB directory ,it took around **35minutes** to complete!:( 

[/code]here is lsmod :
```
Module                  Size  Used by
ide_cd_mod             27652  0 
cdrom                  30680  1 ide_cd_mod
scsi_mod              130748  2 sd_mod,libata
[color="red"]ide_pci_generic         4164  0 [permanent][/color]
ide_core               92696  3 ide_cd_mod,piix,ide_pci_generic

```

You have a number of "ide" entries whereas I don't have any; I think you are also running fujitsu.

Maybe you have the "all_generic_ide" kernel parameter set in your grub menu bootup options; you can confirm with ```
cat /boot/grub/menu.lst | grep -i generic_ide
```

Or if not that, maybe you have the BIOS options for SATA set to "Legacy", or "IDE mode" or "IDE compatiable" or something similar.

---

### Post by deepclutch on 2008-06-12
no I dont have any fujitsu things.no ide setup too.

I think these modules are for the ide port used by my DVD writer drive.
> libata                140136  3 ata_generic,pata_acpi,ata_piix
^these are the modules that are loaded for sata I think.

---

### Post by prshah on 2008-06-12
> **deepclutch said:**
> 
I think these modules are for the ide port used by my DVD writer drive.


My ATAPI (IDE) DVD writer drives are also treated as SCSI (non-ide), eg. /dev/sr0, /dev/sr1.

Just to make it clear: on my system, I have a SATA drive and 2 IDE DVD-RM drives:```

Thu Jun 12 05:11:17 ~:$ lsmod | grep -i ide
video                  19856  0 
output                  4736  1 video
videobuf_dma_sg        14980  2 saa7134_alsa,saa7134
videobuf_core          18820  2 saa7134,videobuf_dma_sg
videodev               29440  1 saa7134
v4l2_common            18304  3 tuner,saa7134,videodev
v4l1_compat            15492  2 saa7134,videodev

```

You can observe from the above that I have no IDE modules loaded, inspite of having IDE drives.

Can you post your "/etc/modules" file? I'm convinced that your SATA drive is being treated as IDE.

Can you also post the output of```
dmesg | grep -i dma
```

---

### Post by sdennie on 2008-06-12
Can you post the output of:

```

sudo hdparm -tT /dev/sda

```

---

### Post by deepclutch on 2008-06-13
> /dev/sda:
 Timing cached reads:   1432 MB in  2.00 seconds = 715.49 MB/sec
 Timing buffered disk reads:   82 MB in  3.02 seconds =  27.16 MB/sec


and :
> /dev/sdb:
 Timing cached reads:   1438 MB in  2.00 seconds = 718.74 MB/sec
 Timing buffered disk reads:  150 MB in  3.03 seconds =  49.55 MB/sec

Let me know the kernel option to enable the full DMA and transfer speed support option ;) 

Thank you!

---

### Post by underground on 2008-06-13
I am trying to copy files between two partitions of the same sata drive and the speed is 11mb/sec.

Is this speed good or it should be higher?

---

### Post by deepclutch on 2008-06-13
^low :cry:

---

### Post by underground on 2008-06-13
Is there any solution to make it higher???

---

### Post by sdennie on 2008-06-13
deepclutch, are both of your disks identical?  The ratio of the hdparm results is very similar to the ratio you'd see if you had one 4200rpm disk and one 7200rpm disk.

---

### Post by deepclutch on 2008-06-13
no! /dev/sda is a 80GB seagate sata and sdb is a  160GB seagate sata!
here are the model info:
> debian:~# cat /proc/scsi/scsi 
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST380215AS       Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: ST3160211AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05

---

### Post by underground on 2008-06-16
I still have a problem with transfer speed and i don't know how to solve it.

Transfer speed between partitions of the same sata disk is about 11MB/sec.
Transfer speed from sata to ide disk is 14-15MB/sec.
Transfer speed from ide to sata is 35MB/sec..

What can i do??
In bios the sata disk storage is set to Native Ide.I can switch it to RAID but then it will not boot in windows..I can't change that all the time...

Please help me.

---

### Post by prshah on 2008-06-16
> **underground said:**
> I still have a problem with transfer speed and i don't know how to solve it.

What can i do??
In bios the sata disk storage is set to Native Ide.I can switch it to RAID but then it will not boot in windows..I can't change that all the time...



Repeated request:
> **prshah said:**
> 
Can you post your "/etc/modules" file? I'm convinced that your SATA drive is being treated as IDE.

Can you also post the output of```
dmesg | grep -i dma
```

---

### Post by underground on 2008-06-16
```
[CODE]hunter@hunter-desktop:~$ dmesg | grep -i dma
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[   28.349617] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   29.348839] ata1: SATA max UDMA/133 abar m1024@0xfbcffc00 port 0xfbcffd00 irq 16
[   29.348842] ata2: SATA max UDMA/133 abar m1024@0xfbcffc00 port 0xfbcffd80 irq 16
[   29.348845] ata3: SATA max UDMA/133 abar m1024@0xfbcffc00 port 0xfbcffe00 irq 16
[   29.348847] ata4: SATA max UDMA/133 abar m1024@0xfbcffc00 port 0xfbcffe80 irq 16
[   29.843266] ata1.00: ATA-7: WDC WD4000AAKS-00TMA0, 12.01C01, max UDMA/133
[   29.844091] ata1.00: configured for UDMA/133
[   30.488067] ata2.00: ATAPI: Optiarc DVD RW AD-7191S, 1.01, max UDMA/100
[   30.654796] ata2.00: configured for UDMA/100
[   32.279444] ata5: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 17
[   33.537138]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[   34.667525] hda: UDMA/100 mode selected
[   34.667764] hdb: UDMA/66 mode selected
hunter@hunter-desktop:~$ 

```[/CODE]

---

### Post by underground on 2008-06-16
And here is the /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
```

if you want anything else tell me.

---

### Post by zgornel on 2008-06-16
> **deepclutch said:**
> and :


Let me know the kernel option to enable the full DMA and transfer speed support option ;) 

Thank you!

Transfer speeds are within normal range and they look configured correctly. If you would have a DMA problem you would not get over 5 MB/s. If your 10GB directory had a lot of small files (music for example) it might take that long. Maybe you were reading/writing to the hard drives with another application ...

---

### Post by prshah on 2008-06-17
> **underground said:**
> 
```
# /etc/modules: kernel modules to load at boot time.
lp
sbp2
```


Try commenting out the sbp2 line by placing a "#" in front of it and restarting. Any improvement? If not, remove the "#" and restart from the line.

---

### Post by underground on 2008-06-17
> **prshah said:**
> Try commenting out the sbp2 line by placing a "#" in front of it and restarting. Any improvement? If not, remove the "#" and restart from the line.

The only improvement i noticed is that the transfer speed from sata to ide is 30mb/sec but between partitions of the same sata disk is only 20mb/sec.Any other setting i should change??

---

### Post by ruohis- on 2008-07-07
Any solutions yet?

I have similar problem too. My Seagate SATA hard drive is very slow. Ubuntu 8.04 system boots up very quickly, but copying files to another folder or partition takes time. Transfer speed is approx. 5 MB/s. I have googled a lot, but no solutions found yet. This thread, I think, was the closest to describe my problem.

Here is some info from my system:

Mainboard: [Asus P5E-VM HDMI LGA-775 micro-ATX]("http://www.asus.com/products.aspx?modelmenu=1&model=1912&l1=3&l2=11&l3=584&l4=0") 
Prosessor: Intel Q6600
Hard drive: Seagate Barracuda 7200.10 320GB Serial-ATA-II

lspci:
```
00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

lsmod:
```
Module                  Size  Used by
ipv6                  267780  14 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  3 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         344728  6 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
atl1                   36364  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mii                     6400  1 atl1
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              25492  1 
psmouse                40336  0 
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               7940  0 
agpgart                34760  3 drm,intel_agp
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
evdev                  13056  4 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
pata_jmicron            7040  0 
ata_generic             8324  0 
ata_piix               19588  2 
usbhid                 31872  0 
hid                    38784  1 usbhid
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
floppy                 59588  0 
pata_acpi               8320  0 
libata                159344  4 pata_jmicron,ata_generic,ata_piix,pata_acpi
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3
```

/etc/modules:
```
fuse
lp
sbp2
```

dmesg | grep -i dma:
```
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[   24.351431] ata1: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 22
[   24.351433] ata2: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 22
[   24.557466] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[   24.623993] ata1.00: configured for UDMA/133
[   24.790236] ata3: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 22
[   24.790238] ata4: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 22
[   25.122090] ata5: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[   25.122093] ata6: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[   25.440746] ata5.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.03, max UDMA/66
[   25.612446] ata5.00: configured for UDMA/66

```

sudo hdparm -tT /dev/sda:
```
/dev/sda:
 Timing cached reads:   6080 MB in  2.00 seconds = 3042.16 MB/sec
 Timing buffered disk reads:  210 MB in  3.02 seconds =  69.64 MB/sec

```
-> I thing this result is very good, but HD to HD is only 5 MB/s.

Model info (/proc/scsi/scsi):
```
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3320620AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVD-RAM GSA-H55N Rev: 1.03
  Type:   CD-ROM                           ANSI  SCSI revision: 05
```

Can anyone help me please? I am new Linux user and this is too difficult problem for me to solve by myself. If this turns out to be simply a hardware compatibility issue, I like to know, what I have to change?

**Solved!**
My hard drive jumper setting was wrong. It was set to limit data transfer rate to 1.5 Gbits per second instead of SATA speed autonegotiation (3.0 Gbits per second). Now transfer speed is approx. 24 MB/s (folder to folder).

---

