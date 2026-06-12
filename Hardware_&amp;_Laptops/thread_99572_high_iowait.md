---
title: "high iowait"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by denkedran on 2005-12-05
Hi folks,

don't know if it's normal and i have to live with it but perhaps someone could help me.
i detect a very high iowait whenever i start a program. this is causing a very lazy behaviour.
An example:
when i start gedit first time in a session it tooks 10s to come up including heavy iowait (nearly 100%)
my system:
AMP athlon xp 2200+
256 MB DDR Ram
K7s5a Mainboard with SIS 735 chipset
Kernelversion: 2.6.12-10-k7
hdparm -v /dev/hda shows:
```
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 234493056, start = 0
```
same for /dev/hdc
hdparm -tT shows:
```
/dev/hda:
 Timing cached reads:   600 MB in  2.00 seconds = 299.75 MB/sec
 Timing buffered disk reads:   32 MB in  3.07 seconds =  10.43 MB/sec
/dev/hdc:
 Timing cached reads:   700 MB in  2.01 seconds = 348.49 MB/sec
 Timing buffered disk reads:   90 MB in  3.11 seconds =  28.94 MB/sec
```
<br>
cat /proc/interrupts shows:
```
          CPU0
  0:    2119898    IO-APIC-edge  timer
  1:       3992    IO-APIC-edge  i8042
  7:          0    IO-APIC-edge  parport0
  8:          1    IO-APIC-edge  rtc
  9:          1   IO-APIC-level  acpi
 10:          0    IO-APIC-edge  MPU401 UART
 14:      62237    IO-APIC-edge  ide0
 15:      24942    IO-APIC-edge  ide1
 16:     280280   IO-APIC-level  nvidia
 18:        539   IO-APIC-level  SiS SI7012
 19:      63726   IO-APIC-level  ohci_hcd:usb1, eth1
 23:          0   IO-APIC-level  ohci_hcd:usb2
NMI:          0
LOC:    2119118
ERR:          0
MIS:          0

```
lsmod shows:
```
Module                  Size  Used by
binfmt_misc            11592  1
rfcomm                 38748  1
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
ipv6                  252544  15
af_packet              22088  2
tsdev                   7872  0
snd_mpu401              6408  1
snd_mpu401_uart         7360  1 snd_mpu401
snd_rawmidi            25056  1 snd_mpu401_uart
snd_seq_device          8524  1 snd_rawmidi
analog                 11680  0
gameport               14920  1 analog
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
snd_intel8x0           33344  3
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  3 snd_pcm_oss
snd_pcm                89032  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  14 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  3 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm
i2c_sis630              7628  0
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
dm_mod                 58044  1
evdev                   9728  0
it87                   26336  0
eeprom                  7504  0
i2c_sensor              3456  2 it87,eeprom
i2c_isa                 2048  0
i2c_sis96x              5316  0
i2c_core               21328  7 i2c_acpi_ec,i2c_sis630,it87,eeprom,i2c_sensor,i2c_isa,i2c_sis96x
nvidia               3711172  20
agpgart                34888  1 nvidia
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  5
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  1 thermal
fan                     4548  0
usbhid                 35552  0
8139too                25728  0
8139cp                 19776  0
mii                     5760  2 8139too,8139cp
tulip                  50272  0
dmfe                   21212  0
ohci_hcd               20740  0
usbcore               118396  3 usbhid,ohci_hcd
ide_cd                 41732  1
cdrom                  39904  1 ide_cd
ide_disk               18560  8
ide_generic             1472  0
sis5513                16392  1
ide_core              139028  4 ide_cd,ide_disk,ide_generic,sis5513
unix                   27248  667
fbcon                  39104  0
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon
vesafb                  8088  0
cfbcopyarea             4672  1 vesafb
cfbimgblt               3008  1 vesafb
cfbfillrect             3968  1 vesafb
softcursor              2496  1 vesafb
capability              4808  0
commoncap               6912  1 capability

```

---

### Post by elvislu on 2006-02-27
I'm suffering from the same problem that the constant IOWAIT draws my computer down. I have 265m RAM, is it inadequate for ubuntu breezy? Any ideas?

---

### Post by mjwood0 on 2006-02-27
10 MB/Sec for buffered read is very bad IMO.  I'm not at my computer now, but that seems very low...

---

### Post by MrMichaelWill on 2006-07-24
I have the same issue on a system with the SIS 5513 IDE onboard chipset. CPU is mostly idle waiting for I/O. hdparm reports 15 to 18 MB/s on the master/slave pair of the two IDE drives.

root@mwill-desktop:~# hdparm -v /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78165360, start = 0

/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0
root@mwill-desktop:~# hdparm -tT /dev/hdb

/dev/hdb:
 Timing cached reads:   2364 MB in  2.00 seconds = 1181.93 MB/sec
 Timing buffered disk reads:   54 MB in  3.06 seconds =  17.67 MB/sec
root@mwill-desktop:~# hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   2344 MB in  2.00 seconds = 1171.93 MB/sec
 Timing buffered disk reads:   46 MB in  3.09 seconds =  14.90 MB/sec

---

### Post by Sam Lars on 2008-02-14
Using UDMA5

/dev/hda:
 Timing cached reads:   450 MB in  2.01 seconds = 224.18 MB/sec
 Timing buffered disk reads:   64 MB in  3.04 seconds =  21.07 MB/sec

I have 757 MB of RAM... the more the better.  If you plan on doing a lot at once, you'll need a lot of RAM to avoid heavy and slow disk usage.
I don't think that kind of start time is that unusual, especially with 256...

---

### Post by dirk_k on 2008-03-20
I had the same problem with the high iowait:
- (very) slow disk access of files (copying files to /dev/null at around 10-15MB/s), but hdparm showed normal numbers (1150MB/s cached reads, 57MB/s buffered disk reads).
- slow starting of programs
- slow switching between programs: it seemed like I only had 256MB or so because it seemed like it was swapping or something, but there was hardly any disk access.
My system: AMD Athlon X2 @ 2.25GHz, 1GB (2x512, DDR2-800, CL4), 320GB SATA Seagate Barracuda 7200.10, Abit NF-M2 NView (onboard VGA, 64MB video memory)

I now am using the kernel from hardy and the system seems much more responsive!
So for all gutsy users having the high iowait problem try the upgrade. See for info on this:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

Success.

---

### Post by gatopeich on 2008-07-20
Wait before upgrading blindly!
I was happily using hardy until recently. The "high iowait" issue just (re)appeared with one of the latest so-called "security updates", somewhere around 2.6.24-19.34. I am trying to roll back a little bit until my system becomes responsive again...
I have seen the issue coming and going for a couple years now, I'd say there is something subtle in kernel configuration, and I have even seen it happen on a 1GB-RAM system with NO swap (with some really bad custom kernel build).

> **dirk_k said:**
> 
...
I now am using the kernel from hardy and the system seems much more responsive!
So for all gutsy users having the high iowait problem try the upgrade. See for info on this:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

Success.

---

