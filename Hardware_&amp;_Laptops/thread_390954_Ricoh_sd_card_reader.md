---
title: "Ricoh sd card reader"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by dixon on 2007-03-22
I can't get work my internal SD card reader
```
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
```I have compiled and running module sdricoh_cs
```
dixon@dixon-laptop:~$ lsmod | grep sd
sdricoh_cs              9480  0 
mmc_core               27780  1 sdricoh_cs
tsdev                   8896  0 
pcmcia                 39596  1 sdricoh_cs

```dmesg
```
[  152.148000] pccard: PCMCIA card inserted into slot 0
[  152.148000] pcmcia: registering new device pcmcia0.0

```fdisk -l
```
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3693    29663991    7  HPFS/NTFS
/dev/hda2            3694        4870     9454252+   5  Extended
/dev/hda5            3694        3783      722893+  82  Linux swap / Solaris
/dev/hda6            3784        4870     8731296   83  Linux

```Do I miss some other module or what? Has anybody tried the sdricoh_cs module?

---

### Post by Black16V on 2007-04-03
HI,

can you post the required packages and the steps you have done... i tryin to compile it but always fails...

---

### Post by dixon on 2007-05-17
```

sudo aptitude install subversion
svn co https://sdricohcs.svn.sourceforge.net/svnroot/sdricohcs sdricohcs
cd sdricohcs/sdricoh_cs/
```[quote="EvilMonkey"]
-Open the sdricoh_cs.c file
-find the reference to protocol.h
-comment out all the if kernel_version stuff around it
-make sure that sd.h is not commented out
[/quote]
```

make
sudo make install
sudo modprobe sdricoh_cs

```It should work then, but not for me, but I think I'm the only one :\

---

### Post by ToniCipriani on 2007-06-12
I got it to work, but not as nice as USB keys.

Did exactly the thing to get the card reader driver compiled and installed, then modprobed it.

Added this to /etc/fstab:
```

/dev/mmcblk0p1  /media/mmc   auto    defaults,sync,iocharset=utf8,user,noauto  0       0
```

But now every time I need to use it, I need to mount it manually:

```
mount /dev/mmcblk0p1
```

It works, but I want to get it so that when a card is plugged in, it automatically shows up in GNOME. Wonder if anybody got this to work.

---

### Post by tl2050 on 2007-11-05
This may be a few months too late, but I just spent about an hour figuring this out, thanks to you all and a couple of other posters. I have the "Ricoh Co Ltd RL5c476 II (rev a9)" sd chipset on my gateway 4635GZ notebook. I believe the key is to include "tifm_sd" in /etc/modules as well as run the sdricoh_cs driver. that should make it auto-mount and work just like it did under the factory windoze install.

good luck!

---

### Post by dixon on 2007-11-05
I can't get it working even with the tifm_sd module loaded :(

lsmod | grep tifm_sd
```

tifm_sd                12808  0 
tifm_core              11268  1 tifm_sd
mmc_core               28420  2 tifm_sd,sdricoh_cs

```

lsmod | grep sdricoh_cs
```

sdricoh_cs             11916  0 
mmc_core               28420  2 tifm_sd,sdricoh_cs
pcmcia                 41388  1 sdricoh_cs

```

whole lsmod
```

Module                  Size  Used by
sdricoh_cs             11916  0 
pcmcia                 41388  1 sdricoh_cs
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  8 
af_packet              24840  2 
binfmt_misc            12936  1 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
dock                   10656  0 
video                  18060  0 
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
button                  8976  0 
battery                11012  0 
tifm_sd                12808  0 
tifm_core              11268  1 tifm_sd
mmc_core               28420  2 sdricoh_cs,tifm_sd
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
ipw2200               149320  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ieee80211              35656  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
xpad                    9988  0 
iTCO_wdt               11940  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27532  4 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                39952  0 
serio_raw               8068  0 
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34580  0 
intel_agp              25620  1 
agpgart                35016  2 drm,intel_agp
pci_hotplug            32704  1 shpchp
evdev                  11136  8 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
8139cp                 25088  0 
ata_piix               17540  3 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
vga16fb                15500  1 
vgastate               11008  1 vga16fb
fbcon                  41760  72 
tileblit                3584  1 fbcon
font                    9344  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit

```

Output of dmesg, when I insert sd card
```

[  264.704000] pccard: PCMCIA card inserted into slot 0
[  264.704000] pcmcia: registering new device pcmcia0.0

```

Any other ideas? Please help :(

---

### Post by tl2050 on 2007-11-05
the only difference I notice is that when I grep tifm_sd and sdricoh_cs, I have an added entry:

lsmod | grep tifm_sd
tifm_sd                12808  0
mmc_core               28420  3 mmc_block,sdricoh_cs,tifm_sd
tifm_core              11268  1 tifm_sd


lsmod | grep sdricoh_cs
sdricoh_cs             11916  0
mmc_core               28420  3 mmc_block,sdricoh_cs,tifm_sd
pcmcia                 41388  1 sdricoh_cs

I'm not sure where the mmc_block comes from, but it does mount. Apparently I was wrong last night when I said it works perfectly, as it seems to only mount as read-only, which makes it still useless. I'll keep giving it a shot, but I would go back and start over with only sdricoh and tifm_sd and move on from there. 

Good Luck!

---

### Post by dixon on 2007-11-06
I think writeable is still experimental. If you want to allow it you have to modprobe the module like this
```

sudo modprobe sdricoh_cs write=1

```

---

