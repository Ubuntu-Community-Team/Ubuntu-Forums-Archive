---
title: "DMA woes"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by jiussa on 2007-03-25
Hi, using Ubuntu 6.1.

I dual boot between WinXP on hda and Ubuntu on hdb. I'm tyrying to enable dma on both hard drives to speed up access and general performance.

Here's the relevant part of **/etc/hdparm.conf**:

```

/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
	dma = on
	io32_support = 1
#	keep_settings_over_reset = on
#	keep_features_over_reset = on
}

/dev/hdb {
#	mult_sect_io = 16
#	write_cache = off
	dma = on
	io32_support = 1
#	keep_settings_over_reset = on
#	keep_features_over_reset = on
}
```

And the results of running **hdparm -i** on both my drives:
```

root@josephs-box:~# hdparm -i /dev/hda

/dev/hda:

 Model=ST3160215A, FwRev=3.AAC, SerialNo=6RA02CNJ
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

root@josephs-box:~# hdparm -i /dev/hdb

/dev/hdb:

 Model=WDC WD400BB-55HEA0, FwRev=13.03G13, SerialNo=WD-WMAJ71442316
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=58
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=78165360
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode


```

Immediately after boot if I run hdparm on either drive it reports that dma is enabled. However if I, for example, run **hdparm -tT /dev/hda** and then check the dma of hdb it is disabled. The reverse is also true.

I read in another thread that it may have something to do with which kernel services are running. Here is the results of **lsmod**:
```

Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
ipv6                  272288  8 
af_packet              24584  2 
nls_cp437               6912  1 
ntfs                  112116  1 
lp                     12964  0 
tsdev                   9152  0 
usbhid                 45152  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
sis900                 25856  0 
analog                 12960  0 
floppy                 63044  0 
i2c_sis96x              6660  0 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
shpchp                 42144  0 
mii                     6912  1 sis900
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
gameport               17160  1 analog
i2c_core               23424  2 i2c_ec,i2c_sis96x
pcspkr                  4352  0 
evdev                  11392  1 
pci_hotplug            32828  1 shpchp
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
sis_agp                 9860  1 
agpgart                34888  1 sis_agp
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
sis5513                15368  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

Strangely enough, the conents of **/etc/modules** is as follows:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```

And that's it. So obviously modules are getting loaded, but not based on the contents of /etc/modules.

Anyway, I'm not sure if this stuff with modules is relevant to my main concern which is getting dma running on both drives. Can anybody help?

Thanks

---

### Post by jiussa on 2007-03-25
Anyone?

---

### Post by jiussa on 2007-03-26
Bump

---

### Post by jiussa on 2007-03-29
Still unable to solve my problem.

In case it helps here are the relevant bits of /var/log/dmesg:

```

joseph@josephs-box:/var/log$ cat dmesg | grep dma
[17179574.056000]  hda:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179574.516000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179574.972000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179574.972000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.432000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.432000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.892000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.892000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179610.224000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179610.224000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179610.224000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179610.224000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179610.256000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179610.256000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179610.256000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179610.256000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }

```

Thanks

---

### Post by jiussa on 2007-03-29
> **jiussa said:**
> Still unable to solve my problem.

In case it helps here are the relevant bits of /var/log/dmesg:

```

joseph@josephs-box:/var/log$ cat dmesg | grep dma
[17179574.056000]  hda:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179574.516000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179574.972000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179574.972000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.432000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.432000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.892000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.892000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179610.224000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179610.224000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179610.224000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179610.224000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179610.256000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179610.256000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179610.256000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179610.256000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }

```

Thanks

Sorry, here's a more complete set or results from dmesg:
```

joseph@josephs-box:~$ cat /var/log/dmesg | grep -i dma
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179571.600000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179571.600000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[17179571.600000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[17179573.884000] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[17179573.908000]  hda:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179574.368000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179574.824000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179574.824000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.284000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.284000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.744000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.744000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.744000] hdb: DMA disabled
[17179575.980000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[17179575.996000] hdd: ATAPI 48X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179609.832000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179609.832000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179609.836000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179609.836000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179609.868000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179609.868000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179609.868000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179609.868000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179609.868000] hda: DMA disabled
[17179640.968000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179640.968000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179641.076000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179641.752000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179641.752000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179642.412000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179642.412000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179643.112000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179643.112000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179643.112000] hdb: DMA disabled

```

---

