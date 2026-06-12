---
title: "[SOLVED] SATA Speed Problem"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by satreth on 2008-01-25
Hello,  
I have a speed problem with my SATA disk. Hdparm -Tt gives me the following output:
> /dev/sda:
 Timing cached reads:   1128 MB in  2.00 seconds = 563.34 MB/sec
 Timing buffered disk reads:    8 MB in  3.24 seconds =   2.47 MB/sec
I'm running Hardy Heron with the 2.6.24-5-generic kernel on a Asus Pundit-R. The motherboard is an Asus P4R8L with an ATI IXP chipset. The lspci output is
> 00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon 9100 IGP Host Bridge [1002:5833] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc Radeon 9100 IGP AGP Bridge [1002:5838]
00:13.0 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #1 [1002:4347] (rev 01)
00:13.1 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #2 [1002:4348] (rev 01)
00:13.2 USB Controller [0c03]: ATI Technologies Inc EHCI USB Controller [1002:4345] (rev 01)
00:14.0 SMBus [0c05]: ATI Technologies Inc SMBus [1002:4353] (rev 18)
00:14.1 IDE interface [0101]: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349]
00:14.3 ISA bridge [0601]: ATI Technologies Inc Unknown device [1002:434c]
00:14.4 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:4342]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon 9100 IGP [1002:5834]
02:08.0 Ethernet controller [0200]: 3Com Corporation 3Com 3C920B-EMB-WNM Integrated Fast Ethernet Controller [10b7:9202] (rev 40)
02:0c.0 CardBus bridge [0607]: ENE Technology Inc CB-710/2/4 Cardbus Controller [1524:1411] (rev 02)
02:0c.1 FLASH memory [0501]: ENE Technology Inc CB710 Memory Card Reader Controller [1524:0510]


The disk is a
> Model Family:     Hitachi Deskstar 7K250 series
Device Model:     HDS722580VLSA80
Firmware Version: V32OA63A


the pata-atiixp module is loaded and used by libata.
I found a suspect line in messages (dmesg) about the ada devices
> 
Jan 25 20:28:20 desk kernel: [   27.162472] ata2.00: ATA-6: HDS722580VLSA80, V32OA63A, max UDMA/100
Jan 25 20:28:20 desk kernel: [   27.162478] ata2.00: 160836480 sectors, multi 16: LBA48 
Jan 25 20:28:20 desk kernel: [   27.162500] ata2.00: simplex DMA is claimed by other device, disabling DMA


Any ideas or tips? Did I miss something?
Thanx

---

### Post by logos34 on 2008-01-25
what does 

sudo hdparm -v -i /dev/sda

show?

---

### Post by satreth on 2008-01-26
The output of the command is:
> 
/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 10011/255/63, sectors = 160836480, start = 0

 Model=HDS722580VLSA80                         , FwRev=V32OA63A
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=7938kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160836480
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2,3,4,5,6

 * signifies the current active mode


---

### Post by logos34 on 2008-01-26
> **satreth said:**
> The output of the command is:

hmm, in the top section I don't see a line '[B]using_dma    =  1 (on)',
[/B]
and lspci shows
> Jan 25 20:28:20 desk kernel: [ 27.162500] ata2.00: simplex DMA is claimed by other device, disabling DMA

so maybe that's the problem.

But it says at the bottom:
> UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5

...

* signifies the current active mode



try 

**sudo hdparm -d1 /dev/sda**

and rerun the test a few times

---

### Post by satreth on 2008-01-27
always gives me an error.

```

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

---

### Post by logos34 on 2008-01-27
maybe hdparm can't set dma on sata drives--it's really for IDE drives (although it can be used to get info as you've been doing).

get **sdparm**, then try again

sudo apt-get install sdparm

man sdparm

ADD: I just checked the man page and I'm not sure how you enable dma with that tool.  TBH, I'm not sure that's the problem anyway...maybe it's something to do with a driver/module bug, or perhaps it's a firmware issue (if it needs flashing/updating, see hitachi website).

---

### Post by satreth on 2008-01-27
Hi, 
as you said I did not find any command to change the DMA state of the disk with sdparm. I look also for a firmware update but had not much success. 
So I tested some more scenarios. I found out that without the CDROM (PATA cable, master on IDE1)  the speed is way better:
```

 /dev/sda:
 Timing cached reads:   1050 MB in  2.00 seconds = 524.65 MB/sec
 Timing buffered disk reads:  174 MB in  3.03 seconds =  57.43 MB/sec

```
The message in dmesg about the simplex DMA being claimed by another device is gone. Could this be a modules related  problem?

ldmod output is
```

Module                  Size  Used by
xt_limit                3584  8 
xt_tcpudp               4096  13 
ipt_LOG                 7296  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        7576  0 
nf_conntrack_ftp       10144  0 
xt_state                3328  6 
radeon                124192  2 
drm                    81300  3 radeon
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              60132  4 rfcomm,l2cap
ppdev                  10372  0 
ipv6                  267780  12 
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
video                  19728  0 
output                  4736  1 video
dock                   11280  0 
ac                      6916  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
pcmcia                 40876  0 
snd_atiixp             21004  3 
snd_ac97_codec        100516  1 snd_atiixp
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42624  0 
snd_mixer_oss          17664  1 snd_pcm_oss
evdev                  13056  4 
snd_pcm                80644  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
serio_raw               7940  0 
psmouse                40336  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33280  0 
snd_seq_midi            9472  0 
snd_rawmidi            25600  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                53104  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55172  16 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
soundcore               8800  1 snd
i2c_piix4               9612  0 
snd_page_alloc         11272  2 snd_atiixp,snd_pcm
i2c_core               24832  1 i2c_piix4
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ati_agp                 9996  1 
agpgart                34760  2 drm,ati_agp
iptable_nat             8324  0 
nf_nat                 20396  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19080  8 iptable_nat
nf_conntrack           66624  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  1 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
usbhid                 31744  0 
hid                    38528  1 usbhid
sr_mod                 17956  0 
sd_mod                 30592  3 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
pata_atiixp             8960  2 
pata_acpi               8320  0 
3c59x                  46376  0 
mii                     6400  1 3c59x
libata                159344  3 ata_generic,pata_atiixp,pata_acpi
ehci_hcd               37004  0 
ohci_hcd               28036  0 
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
usbcore               145516  4 usbhid,ehci_hcd,ohci_hcd
ssb                    32260  1 ohci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5380  0 
fuse                   50580  1 

```

thx

---

### Post by logos34 on 2008-01-27
> **satreth said:**
> So I tested some more scenarios. I found out that without the CDROM (PATA cable, master on IDE1)  the speed is way better

wait, you said this is a SATA drive (thin cable) ...or is it IDE, on the same cable as the cdrom?

clarify

If it is indeed a SATA, I don't know how disconnecting the cdrom woould affect the drive speed...they're on completely different controllers

---

### Post by satreth on 2008-01-27
The cable of the HD is SATA, while the CDROM is a 40pin PATA, but I Think I found the problem.
Apparently it is related to the modules.
Found [this]("http://ubuntuforums.org/showthread.php?t=435706") other thread.
So I blacklisted ata_generic and added pata_atiixp to /etc/initramfs-tools/modules
```

pata_atiixp
blacklist ata_generic

```
and recreated the initramfs with
```

sudo update-initramfs -u 

```
and, after a reboot, the speed was better:
```

$ sudo htparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   948 MB in  2.00 seconds = 474.01 MB/sec
 Timing buffered disk reads:  174 MB in  3.03 seconds =  57.44 MB/sec

```

However I saw around that the 474MB/sec is not so good, or is this just my disk/controller?

thanks

---

### Post by logos34 on 2008-01-27
yeah, driver/module issue makes more sense...

Those speeds seem a little low for sata...cached read seems way low, disk read of ~57 mb is close to average (just for comparison, my IDE ata-133 drive averages ~500 mb/s cached reads, and ~50 mb/s disk reads.  My other drive, nearly identical, averages ~975 mb/s caced reads, and about the same disk reads.  Go figure).

If you look at the Hitachi spec sheets you'll hardly any diff in the performance between the SATA and PATA versions of a given drive model, so it's not surprising you're getting figures like that.

---

### Post by satreth on 2008-01-27
Thanks!
:)

---

### Post by avsa242 on 2008-02-05
> **satreth said:**
> The cable of the HD is SATA, while the CDROM is a 40pin PATA, but I Think I found the problem.
Apparently it is related to the modules.
Found [this]("http://ubuntuforums.org/showthread.php?t=435706") other thread.
So I blacklisted ata_generic and added pata_atiixp to /etc/initramfs-tools/modules
```

pata_atiixp
blacklist ata_generic

```
and recreated the initramfs with
```

sudo update-initramfs -u 

```


Thanks...this was really starting to drive me crazy. Mine uses the atiixp module too and any reads/writes from the cdrom were dog slow and hung the system each time data was being transferred.

Cheers,
Jesse Burt

---

