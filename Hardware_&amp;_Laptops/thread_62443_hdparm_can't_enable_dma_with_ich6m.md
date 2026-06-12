---
title: "hdparm can't enable dma with ich6m"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by rob666 on 2005-09-04
Hi,
I can't get dma enable on my dvd or hard disk. I'll consentrate this post on the harddrive because I figure once that works the dvd should work too. Now I have ICH6-M so it's actually supposed to support SATA, but the hard disk is ide.
first here's the output for hdparm -d1 /dev/sda1:

/dev/sda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Here's my hdparm -i /dev/sda1 output

[PHP]/dev/sda1:

 Model=WDC WD800VE-75HD09.0, FwRev=09.0, SerialNo=
 Config={ }
 RawCHS=9729/255/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=9729/255/63, CurSects=0, LBA=no
 IORDY=no
 PIO modes:  pio0
 AdvancedPM=no

 * signifies the current active mode[/PHP]

It makes no indication that dma is even available however in dmesg | grep ata says that I have udma/133:

[PHP]libata version 1.10 loaded.
ata_piix version 1.03
ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xFFA0 irq 14
ata1: dev 0 cfg 49:2f00 82:346b 83:5b09 84:4003 85:3469 86:1809 87:4003 88:203f
ata1: dev 0 ATA, max UDMA/100, 156301488 sectors:
ata1(0): applying bridge limits
ata1: dev 0 configured for UDMA/100
scsi0 : ata_piix
ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xFFA8 irq 15
ata2: dev 0 cfg 49:0f00 82:4218 83:5000 84:4000 85:4218 86:1000 87:4000 88:0407
ata2: dev 0 ATAPI, max UDMA/33
ata2(0): applying bridge limits
ata2: dev 0 configured for UDMA/33
scsi1 : ata_piix
EXT3-fs: mounted filesystem with ordered data mode.
ata1: status=0x51 { DriveReady SeekComplete Error }
ata1: error=0x04 { DriveStatusError }
ata1: status=0x51 { DriveReady SeekComplete Error }
ata1: error=0x04 { DriveStatusError }
ata1: status=0x51 { DriveReady SeekComplete Error }
ata1: error=0x04 { DriveStatusError }
ata1: status=0x51 { DriveReady SeekComplete Error }
ata1: error=0x04 { DriveStatusError }
ata1: status=0x51 { DriveReady SeekComplete Error }
ata1: error=0x04 { DriveStatusError }[/PHP]

the last error messages show up at boot as: 

[PHP]Sep  3 02:21:22 localhost kernel: ide0: I/O resource 0x1F0-0x1F7 not free.
Sep  3 02:21:22 localhost kernel: ide0: ports already in use, skipping probe
Sep  3 02:21:22 localhost kernel: ide1: I/O resource 0x170-0x177 not free.
Sep  3 02:21:22 localhost kernel: ide1: ports already in use, skipping probe[/PHP] 

This is appartently a problem related to which modules are directly in the kernel and which one's are added afterwards. I don't know what this has to do with hdparm, but I'm guessing this is confusion hdparm. here is my lsmod output:

[PHP]Module                  Size  Used by
speedstep_centrino      7892  1
proc_intf               3908  0
freq_table              4004  1 speedstep_centrino
cpufreq_userspace       4348  1
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
button                  6480  0
battery                 9988  0
container               4320  0
ac                      4676  0
asus_acpi              11572  0
ipv6                  257760  9
af_packet              21992  2
arc4                    1728  1
ieee80211_crypt_wep     5220  1
ipw2200               133100  0
firmware_class          9984  1 ipw2200
ieee80211              36388  1 ipw2200
ieee80211_crypt         5960  2 ieee80211_crypt_wep,ieee80211
yenta_socket           21344  0
pcmcia_core            57984  1 yenta_socket
sk98lin               171136  0
i2c_i801                8364  0
i2c_core               22320  1 i2c_i801
hw_random               5300  0
ehci_hcd               32708  0
usbhid                 31936  0
uhci_hcd               32816  0
usbcore               119000  4 ehci_hcd,usbhid,uhci_hcd
shpchp                 99172  0
pci_hotplug            33488  1 shpchp
snd_hda_intel          17472  0
snd_hda_codec          72224  1 snd_hda_intel
snd_pcm_oss            54016  0
snd_mixer_oss          20320  1 snd_pcm_oss
snd_pcm                94632  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26148  1 snd_pcm
snd                    57540  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9988  2 snd_hda_intel,snd_pcm
intel_agp              22140  1
agpgart                33608  2 intel_agp
pcspkr                  3496  0
rtc                    12472  0
md                     47440  0
dm_mod                 59420  1
capability              4648  0
commoncap               7712  1 capability
video1394              18732  0
ohci1394               34596  1 video1394
raw1394                30732  0
sbp2                   23816  0
ieee1394              108312  4 video1394,ohci1394,raw1394,sbp2
joydev                  9664  0
tsdev                   7520  0
evdev                   9344  1
psmouse                21320  0
mousedev               11288  1
parport_pc             37252  0
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_generic             1312  0
ide_disk               20416  0
ide_cd                 41700  0
piix                   10340  0
ide_core              129356  4 ide_generic,ide_disk,ide_cd,piix
ext3                  137256  1
jbd                    60536  1 ext3
mbcache                 8356  1 ext3
ahci                   10724  0
sr_mod                 17188  0
cdrom                  40220  2 ide_cd,sr_mod
sd_mod                 17776  3
sg                     38400  0
ata_piix                9124  4
libata                 49316  2 ahci,ata_piix
scsi_mod              127552  6 sbp2,ahci,sr_mod,sd_mod,sg,libata
unix                   28276  508
thermal                13320  0
processor              22452  2 speedstep_centrino,thermal
fan                     4388  0
fbcon                  37504  71
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  1
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb[/PHP] 

I've read some suggestions that I edit my /etc/modules file to load ata_piix and piix before the ide modules, but that hasn't worked.

[PHP]ata_piix
piix
ide-core
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
raw1394
video1394[/PHP] 


I have kernel 2.6.10-5-686 running as 2.6.11 didnt work, so I'm not sure what modules ubuntu has built in there or what's added later. I assume dma is supported though as ubuntu suggests running hdparm -d1 on it's wiki. 

I did find an apparent fix for this, but it involves building a new kernel. I don't feel very comfortable doing that since I screwed up a few already and the patch seems iffy. On top of that I don't really want to since I'd have to reinstall the graphic driver, wireless, sound and I wouldn't know how to built it exactly like the 686 version as there's only a 2.6.10 linux-source available.
Here's a to the link: [http://www.linuxquestions.org/questions/history/340897](http://www.linuxquestions.org/questions/history/340897)
Lastly in my bios dma is set to auto, 32 bit is on. This is an asus z63a laptop and there aren't any options in the bios for the sata controller.
Anyway hope this post wasn't too long. Would appreciate any help.

---

### Post by tseliot on 2005-09-06
I suggest you to solve your problem once for all:

Follow my guide (it's for newbies) to compile a kernel with DMA enabled (it solved my problems):

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

Don't be afraid of compiling your 1st kernel, it's very easy and everything it's explained in the guide.

---

### Post by rob666 on 2005-09-06
Well thanks for you're advice, of course I tried it right away. I was relieved to see that after recompiling the kernel my graphic driver was still working. Sound was down though, but I think that's just a matter of reconfiguring alsa. DMA is still not working, tests showed similar numbers as before, about 30mb/s. I've gathered that there's quite a bit that can go wrong with dma, so I'm not sure we have the same problem. I think my problem is that I have a sata controller and an ide disk. Is that similar to the problem you had? Anyway thanks for your post, at least I managed to compile a kernel that worked.

---

### Post by tseliot on 2005-09-07
Here's my computer:
AMD Athlon™ 64 3500+
ATI RADEON® XPRESS 200P
2 GB DDR-SDRAM
Seagate barracuda 160 Serial ATA 
Maxtor 120gb PATA (with Ubuntu)
Samsung DVD-reader
TS DVD-writer
memory card reader 9in1
Modem 56K
Lan 10/100BT
NVIDIA® GeForce™ 6200 Turbocache 256 MB PCI-Express 16x
Integrated audio 5.1
PS/2 keyboard and mouse
7 USB 2.0 ports 2 FireWire-IEEE-1394

Believe me, my computer really hates Linux.

Did you build DMA into the kernel as I suggest in the guide?

---

### Post by rob666 on 2005-09-07
Yep I'm now running with "Enable DMA only for disks" switched to "n". hdparm /dev/sda still looks like this:

[PHP]/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 80026361856, start = 0[/PHP] 
 
Here's my output for hdparm -I /dev/sda

[PHP]/dev/sda1:

ATA device, with non-removable media
        Model Number:       WDC WD800VE-75HDT0
        Serial Number:      WD-WXE205309172
        Firmware Revision:  09.07D09
Standards:
        Supported: 6 5 4 3
        Likely used: 6
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  156301488
        device size with M = 1024*1024:       76319 MBytes
        device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 50     Queue depth: 1
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x0080)
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
           *    SMART feature set
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
                Automatic Acoustic Management feature set
                SET MAX security extension
           *    Advanced Power Management feature set
           *    DOWNLOAD MICROCODE cmd
           *    SMART self-test
           *    SMART error logging
Security:
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct[/PHP] 

There's a little star next to udma5 which gives me hope that dma is actually working although hdparm says otherwise. Hdparm -I for my dvd doesn't bring any results. 
I've got an intel sonoma processor, and ICH6-m chipset, so I image it'll be running a bit differently than your AMD. 
I don't know, what happens when you hdparm -d 1 /dev/your_hard_disk?
Thanks, rob

---

### Post by tseliot on 2005-09-07
I'm not sure but I've read somewhere that hdparm is not compatible with SATA drives,

---

### Post by rob666 on 2005-09-07
I read that too but fortunately it's an ide drive with a sata controller.

---

### Post by mlord on 2005-09-07
[QUOTE=rob666]I read that too but fortunately it's an ide drive with a sata controller.[/QUOTE]
 Looks to me like both drives (hard disk and optical drive) are using DMA, specifically:

Here is your hard disk (DMA is on):
>ata1: dev 0 ATA, max UDMA/100, 156301488 sectors:
>ata1: dev 0 configured for UDMA/100

Here is your ATAPI (optical) drive (DMA is on):
>ata2: dev 0 ATAPI, max UDMA/33
>ata2: dev 0 configured for UDMA/33

Both drives are using the ata_piix libata driver ("SATA"),
rather than the ancient IDE drivers (which I originally wrote,
years ago).  This is good.

Cheers

---

### Post by tseliot on 2005-09-07
[QUOTE=mlord]Looks to me like both drives (hard disk and optical drive) are using DMA, specifically:

Here is your hard disk (DMA is on):
>ata1: dev 0 ATA, max UDMA/100, 156301488 sectors:
>ata1: dev 0 configured for UDMA/100

Here is your ATAPI (optical) drive (DMA is on):
>ata2: dev 0 ATAPI, max UDMA/33
>ata2: dev 0 configured for UDMA/33

Both drives are using the ata_piix libata driver ("SATA"),
rather than the ancient IDE drivers (which I originally wrote,
years ago).  This is good.

Cheers[/QUOTE]This makes sense if he hasn't got any slowdown while transferring files. He has to tell us if he has this problem.

---

### Post by rob666 on 2005-09-07
Ok,
the test results are in. 
Copying from DVD to hard disk I get up to 7.5 mb/s, everythings very steady. According to System monitor I use up around 20% of cpu and I can use the computer fairly decently.
Copying within the hard disk I get between 8.6 to 19.4mb/s, its very choppy. Cpu is between 10 and 30%, in reality though multitasking is impossible.
So what do you say, is DMA doing it's job?
I guess it would help though if you guys knew my system. I have 1.6 mhz pentium M 915 gm & ICH6-M with 512 mb DDR2 Ram the hard disk is uata 5400 rpms.
Cheers, Rob

P.S nice to hear that ottawas living up to its name as canada's IT hotbed.

---

### Post by tseliot on 2005-09-08
the dma enabled kernel was the last resort. Why do you have to use a SATA controller for PATA drives anyway?

---

### Post by rob666 on 2005-09-08
Well, I guess the moral of this story is:

either the harddisk and bios automatically turn dma on

or

ata_piix automatically turns dma on at boot

whatever the case may be hdparm isn't able to do much anything. As for the SATA controller (which is paradoxically the ide controller) that's just a piece of hardware that came stardard in my laptop, I was able to "choose" which harddisk I wanted and I "chose" an ide harddisk. I guess there's an adapter between the two so that the cables fit. Anyways, thanks to you both for your tips and tricks.
Yours, Rob

---

