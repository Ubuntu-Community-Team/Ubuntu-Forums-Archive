---
title: "USB Experiment board"
date: 2009-10-01
forum: Hardware
---

### Post by theinnercityhippy on 2009-10-01
Hi

I&#7743; working on a project to receive a pulse signal from an old coin acceptor mechanism and convert it to a usb signal so I can build a new jukebox for an autonomous social centre I am involved with.

To do this I have got hold of a USB experiment board as shown here:

[http://www.elexp.com/tst_bkit.htm](http://www.elexp.com/tst_bkit.htm)

It uses the (quite common) CY7C6300A-PC microcontroller to translate input to usb signals on 8 of its pins. There is a driver in the kernel for this chip - cypress_cy7c63 - which I have modprobed in. The problem I am having is that the hardware isn correctly identified and so is not associating with the driver, meaning the endpoints are not exposed in /proc/bus/usb/ (which I have mounted via fstab) and so I cannot read/write any signals to the device.

Is there a way of telling the USB subsytem or HAL to associate the driver when the hardware is inserted? I have searched everywhere to find a solution and am at my wits end :-/

Taking the specific hardware out, it could be a general question as to how to modify hardware id&#347; that lsusb shows and so associate that id with a particular driver.

Here&#347; some output which will hopefully help with this:

```
lsusb

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 0fc5:1222 Delcom Engineering I/O Development Board
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
cat /proc/bus/usb/devices

...output cut...

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 6
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev= 2.06
S:  Manufacturer=Linux 2.6.27-7-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  8 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0fc5 ProdID=1222 Rev= 0.09
S:  Manufacturer=Delcom Engineering
S:  Product=USB IO Controller
S:  SerialNumber=5286
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=250mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)

```

```
lsmod

cypress_cy7c63         11648  0 
ipv6                  263972  14 
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
vboxnetadp             89704  0 
vboxnetflt             96520  0 
vboxdrv               131752  1 vboxnetflt
kvm_amd                33164  0 
kvm                   142912  1 kvm_amd
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_ondemand       14988  2 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
sbs                    19464  0 
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
container              11520  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_ens1371            30880  2 
snd_hda_intel         381488  3 
psmouse                45200  0 
gameport               19468  1 snd_ens1371
serio_raw              13444  0 
pcspkr                 10624  0 
evdev                  17696  6 
snd_ac97_codec        111652  1 snd_ens1371
nvidia               6909268  36 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_seq_dummy          10884  0 
agpgart                42184  1 nvidia
snd_seq_oss            38528  0 
snd_mixer_oss          22784  1 snd_pcm_oss
i2c_core               31892  1 nvidia
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_ens1371,snd_seq_midi
snd_pcm                83204  4 snd_ens1371,snd_hda_intel,snd_ac97_codec,snd_pcm_oss
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29960  2 snd_pcm,snd_seq
snd                    63268  21 snd_ens1371,snd_hda_intel,snd_ac97_codec,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              15328  1 snd
shpchp                 37908  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
pci_hotplug            35236  1 shpchp
wmi                    14504  0 
button                 14224  0 
ext3                  133256  3 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ahci                   37132  4 
pata_amd               18692  0 
forcedeth              61328  0 
ehci_hcd               43276  0 
libata                177312  4 pata_acpi,ata_generic,ahci,pata_amd
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
ohci_hcd               31888  0 
dock                   16656  1 libata
usbcore               148848  4 cypress_cy7c63,ehci_hcd,ohci_hcd
dm_mirror              26880  0 
dm_log                 17924  1 dm_mirror
dm_snapshot            26276  0 
dm_mod                 63432  3 dm_mirror,dm_log,dm_snapshot
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
```

Many thanks for any help anyone can give.

---

