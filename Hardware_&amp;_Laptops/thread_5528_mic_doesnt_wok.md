---
title: "mic doesnt wok"
date: 2004-11-19
forum: Hardware &amp; Laptops
---

### Post by Razvan on 2004-11-19
Hi all

i have a NForce 2 Mobo (AOpen AK79D-1394 ) this thing has the soundstorm-stuff and so on, i believe, it is the standard nforce audio chip, but im not quite shure...because my Device Manger tells me, its from via

anyway...sound worked wonderful, out of the box and so on, just my microphone wont work...it does under window~1

i rocked up all the controls in my sound mixer (it has 2 tabs ... one with  OSS ... one with alsa ) boosted the mic and its connected to the pinky mic input on my mobo

lsmod shows : 

```

root@Razvan:/home/udssr # lsmod
Module                  Size  Used by
proc_intf               3840  0
cpufreq_powersave       1792  0
cpufreq_userspace       5336  0
freq_table              4292  0
button                  6680  0
ac                      4876  0
battery                 9484  0
ipv6                  258116  8
af_packet              22344  2
ohci1394               35268  0
pciehp                 96236  0
shpchp                 99436  0
pci_hotplug            33776  2 pciehp,shpchp
snd_intel8x0           35564  3
snd_ac97_codec         67908  1 snd_intel8x0
snd_pcm_oss            53160  0
snd_mixer_oss          19520  3 snd_pcm_oss
snd_pcm                95332  2 snd_intel8x0,snd_pcm_oss
snd_timer              25028  1 snd_pcm
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
snd_mpu401_uart         7872  1 snd_intel8x0
snd_rawmidi            25088  1 snd_mpu401_uart
snd_seq_device          8136  1 snd_rawmidi
snd                    55524  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mix er_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  3 snd
forcedeth              17472  0
ehci_hcd               30852  0
joydev                  9792  0
tsdev                   7296  0
usbhid                 31680  0
ohci_hcd               21060  0
usbcore               115876  5 ehci_hcd,usbhid,ohci_hcd
nvidia_agp              7772  1
agpgart                33704  2 nvidia_agp
analog                 11808  0
gameport                4672  2 snd_intel8x0,analog
floppy                 59348  0
pcspkr                  3688  0
rtc                    12600  0
lazyfs0d1d25           21704  1
nls_iso8859_1           4096  1
nls_cp437               5760  1
vfat                   14592  1
fat                    46144  1 vfat
md                     48648  0
dm_mod                 57660  1
capability              4616  0
commoncap               7168  1 capability
loop                   16264  0
nvidia               4821236  24
parport_pc             34944  1
lp                     10820  0
parport                40904  2 parport_pc,lp
sbp2                   24072  0
evdev                   9536  0
ieee1394              109304  2 ohci1394,sbp2
ide_cd                 41732  0
mousedev               10316  1
psmouse                19784  0
sr_mod                 17124  0
scsi_mod              122828  2 sbp2,sr_mod
cdrom                  39648  2 ide_cd,sr_mod
reiserfs              241968  3
ext2                   70504  0
ext3                  124712  0
jbd                    61144  1 ext3
mbcache                 9156  2 ext2,ext3
ide_generic             1472  0
ide_disk               18816  6
amd74xx                14108  1
ide_core              136344  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   28272  760
fan                     4044  0
thermal                13072  0
processor              17456  1 thermal
font                    8448  0
vesafb                  6624  0
cfbcopyarea             3776  1 vesafb
cfbimgblt               3136  1 vesafb
cfbfillrect             3712  1 vesafb

``` 

any ideas? thanks in advance, Martin

---

