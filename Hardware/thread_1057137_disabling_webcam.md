---
title: "disabling webcam"
date: 2009-02-01
forum: Hardware
---

### Post by heartwarmer on 2009-02-01
I have an acer travelmate 3275, it has an orbicam (i think),
how do i disable it? as if it's not there.
i dont know what to put in the blacklist file, so if anybody can help me with this, thanks.

---

### Post by Crafty Kisses on 2009-02-01
Not sure what the module is called, but to blacklist what you need, you can run the following command:
```
/etc/modprobe.d/blacklist
```

---

### Post by heartwarmer on 2009-02-01
thanks but i know that, what i need is a way to know the module name.

---

### Post by Crafty Kisses on 2009-02-01
What are the results of this command?
```
lsmod
```

---

### Post by heartwarmer on 2009-02-01
lsmod
Module                Size  Used by
isofs                 40100  0 
udf                   88356  0 
crc_itu_t             10112  1 udf
usb_storage           82752  0 
libusual              30356  1 usb_storage
ipv6                  263972  10 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
af_packet              25728  4 
i915                   38528  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
vmnet                  48580  13 
vmblock                21156  3 
vmci                   58964  0 
vmmon                  78064  0 
acpi_cpufreq           15500  1 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         384176  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
joydev                 18368  0 
arc4                    9984  2 
pcmcia                 43052  0 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
gspca_vc032x           26112  0 
gspca_main             29312  1 gspca_vc032x
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
iwl3945                98804  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               18596  0 
yenta_socket           31756  1 
acer_wmi               19008  0 
rfkill                 17176  2 iwl3945
rsrc_nonstatic         19072  1 yenta_socket
tifm_7xx1              13824  0 
iTCO_vendor_support    11652  1 iTCO_wdt
mac80211              216820  1 iwl3945
videodev               41344  1 gspca_main
pcspkr                 10624  0 
tifm_core              16028  1 tifm_7xx1
evdev                  17696  10 
psmouse                45200  0 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw              13444  0 
led_class              12164  2 iwl3945,acer_wmi
v4l1_compat            22404  1 videodev
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               32392  2 iwl3945,mac80211
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
video                  25232  0 
intel_agp              33724  1 
container              11520  0 
output                 11008  1 video
wmi                    14504  1 acer_wmi
agpgart                42184  3 drm,intel_agp
ac                     12292  0 
battery                18436  0 
button                 14224  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod

sd_mod                 42392  6 

crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  5 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                178208  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  7 usb_storage,libusual,gspca_vc032x,gspca_main,ehci_hcd,uhci_hcd
sky2                   53380  0 
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  7

---

### Post by heartwarmer on 2009-03-29
bump..!!

---

