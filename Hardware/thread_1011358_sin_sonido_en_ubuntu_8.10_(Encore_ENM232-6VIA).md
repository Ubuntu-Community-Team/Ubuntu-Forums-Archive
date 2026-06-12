---
title: "sin sonido en ubuntu 8.10 (Encore ENM232-6VIA)"
date: 2008-12-14
forum: Hardware
---

### Post by gdp.fernando on 2008-12-14
Mi problema es el siguiente:

Tengo una placa de sonido ENCORE ENM232-6VIA es pci, y una integrada que no anda bien por eso compre la encore. Resulta que instale Ubuntu 8.10 y no me anda el sonido y en el 8.04 me andaba aveces cuando tenia ganas. Aca les mando algo de info para ver si me pueden ayudar, gracias!

lspci:

.
.
.
04:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

lsmod:


Module                  Size  Used by
ipv6                  263972  16 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
af_packet              25728  4 
binfmt_misc            16904  1 
i915                   38144  2 
drm                    86056  3 i915
sco                    18308  2 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pci_slot               12552  0 
sbs                    19464  0 
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
container              11520  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_ice1724           101052  3 
snd_ice17xx_ak4xxx     11648  1 snd_ice1724
snd_ac97_codec        111652  1 snd_ice1724
ac97_bus                9856  1 snd_ac97_codec
snd_ak4xxx_adda        16512  2 snd_ice1724,snd_ice17xx_ak4xxx
arc4                    9984  2 
snd_ak4114             17152  1 snd_ice1724
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  4 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss
snd_page_alloc         16136  1 snd_pcm
snd_pt2258             11904  1 snd_ice1724
snd_i2c                13440  2 snd_ice1724,snd_pt2258
rt73usb                30464  0 
snd_seq_dummy          10884  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18816  1 rt73usb
rt2x00lib              36224  2 rt73usb,rt2x00usb
snd_seq_oss            38528  0 
rfkill                 17176  1 rt2x00lib
led_class              12164  1 rt2x00lib
snd_seq_midi           14336  0 
pcspkr                 10624  0 
mac80211              216820  2 rt2x00usb,rt2x00lib
snd_rawmidi            29824  2 snd_ice1724,snd_seq_midi
cfg80211               32392  2 rt2x00lib,mac80211
evdev                  17696  6 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  20 snd_ice1724,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_pt2258,snd_i2c,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
ata_generic            12932  0 
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
usb_storage            81728  1 
ata_piix               24580  2 
libusual               27284  1 usb_storage
pata_acpi              12160  0 
libata                177440  3 ata_generic,ata_piix,pata_acpi
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
ehci_hcd               43404  0 
usbcore               149360  8 rt73usb,rt2x00usb,usbhid,usb_storage,libusual,uhci_hcd,ehci_hcd
r8169                  36100  0 
mii                    13440  1 r8169
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

**************************************************************

modinfo soundcore:

filename:       /lib/modules/2.6.27-10-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-10-generic SMP mod_unload modversions 586

---

### Post by faktorqm on 2008-12-15
Aca le conteste a uno recien que tiene el mismo modelo y el mismo problema. [http://ubuntuforums.org/showthread.php?t=1011237](http://ubuntuforums.org/showthread.php?t=1011237) salu2!

---

### Post by Dieter-AR on 2010-06-05
Me pasa exactamente lo mismo, tengo una integrada que dejó de andar y le puse esa placa ENCORE, la cosa es que a veces anda y a veces no, muy inestable, alguien me puede decir como solucionar esto ?

---

