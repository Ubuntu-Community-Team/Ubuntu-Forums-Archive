---
title: "DMA = off. Operation not permited."
date: 2004-11-20
forum: Hardware &amp; Laptops
---

### Post by Kiwi on 2004-11-20
Hi people!
I unable to turn DMA = ON for my IDE DVD and it's working very slow. If I install on IDE  HDD everithing fine. But my IDE HDD very small and too slow. I've checked out this forum and found some solutions for this problem. But it's not working in my computer. I new in Debian linux and really impressed compare RPM linux  what I used before. But I had not this problem on same computer. HDD SATA and IDE DVD.  If somebody knows solution just let me know, please. Thank you.
P.S. This is some data.
#lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Inter face (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (re v 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (re v 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (re v 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (re v 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Contr oller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BA/CA/DB/EB/ER Hub interface to PCI Br idge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 St orage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Co ntroller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02 )
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC '97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 96 00]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Se condary)
0000:02:01.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Control ler
0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
#lsmod
Module                  Size  Used by
proc_intf               3776  0
freq_table              4196  0
cpufreq_userspace       5240  0
cpufreq_powersave       1728  0
button                  6584  0
ac                      4812  0
battery                 9388  0
ipv6                  256996  8
af_packet              22088  2
8139too                25568  0
8139cp                 20256  0
mii                     5056  2 8139too,8139cp
crc32                   4288  2 8139too,8139cp
ohci1394               34884  0
ieee1394              108408  1 ohci1394
snd_intel8x0           35468  3
snd_ac97_codec         67844  1 snd_intel8x0
snd_pcm_oss            52968  0
snd_mixer_oss          19456  3 snd_pcm_oss
snd_pcm                95140  2 snd_intel8x0,snd_pcm_oss
snd_timer              24900  1 snd_pcm
snd_page_alloc         11432  2 snd_intel8x0,snd_pcm
gameport                4608  1 snd_intel8x0
snd_mpu401_uart         7776  1 snd_intel8x0
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8040  1 snd_rawmidi
snd                    55300  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10112  3 snd
piix                   13088  1
ehci_hcd               30756  0
uhci_hcd               31952  0
usbcore               115684  4 ehci_hcd,uhci_hcd
shpchp                 99340  0
pciehp                 96108  0
pci_hotplug            33680  2 shpchp,pciehp
intel_agp              22112  0
intel_mch_agp          10320  1
agpgart                33640  2 intel_agp,intel_mch_agp
floppy                 59156  0
pcspkr                  3592  0
rtc                    12536  0
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
parport_pc             34752  1
lp                     10724  0
parport                40712  2 parport_pc,lp
ide_generic             1408  0
ide_disk               18752  0
ide_cd                 41572  0
ide_core              136120  4 piix,ide_generic,ide_disk,ide_cd
cdrom                  39392  1 ide_cd
tsdev                   7232  0
evdev                   9440  0
mousedev               10220  1
psmouse                19720  0
ext3                  123880  1
jbd                    60824  1 ext3
mbcache                 9092  1 ext3
sd_mod                 21344  3
ata_piix                8004  4
libata                 40292  1 ata_piix
scsi_mod              122508  2 sd_mod,libata
unix                   28080  686
fan                     3980  0
thermal                12976  0
processor              17392  1 thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb
Thank you.

---

### Post by Viro on 2004-11-20
What's the problem you're having?

---

### Post by Kiwi on 2004-11-20
OK. Problem is simple. When I trying to hdparm -d1 /dev/hdc I've got Operation not permited. DMA=off. And I unable to make it ON.

---

### Post by Viro on 2004-11-20
[QUOTE=Kiwi]OK. Problem is simple. When I trying to hdparm -d1 /dev/hdc I've got Operation not permited. DMA=off. And I unable to make it ON.[/QUOTE]
 Dumb question, did you do sudo /sbin/hdparm -d1 /dev/hdc ?

You can't use hdparm as a normal user.

---

### Post by Kiwi on 2004-11-20
Yes. I did. I founf in this forum another thread about same problem.
[http://ubuntuforums.org/showthread.php?t=5271&highlight=dma](http://ubuntuforums.org/showthread.php?t=5271&highlight=dma)
last reply is very promising but I use Intel chipset and can't find out what module I should put in etc/modules. Thank you.

---

