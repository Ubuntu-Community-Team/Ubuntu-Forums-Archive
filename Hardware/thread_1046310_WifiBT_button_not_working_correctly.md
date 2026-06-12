---
title: "Wifi/BT button not working correctly"
date: 2009-01-21
forum: Hardware
---

### Post by v.wochnik on 2009-01-21
Hello.

I noticed, that the wireless lan and bluetooth button is not working correctly. When I press the button, the wifi/bt-chips are disabled by the bios. And that's the point. When I boot with disabled wifi/bt, the kernel modules are not loaded. How can I load them automaticly, although the chips are not enabled?

Here is my lsmod, when the chips are enabled:

```
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  4 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44432  2 
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  16 rfcomm,bnep
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
evdev                  17696  10 
serio_raw              13444  0 
iwl3945                98804  0 
snd_seq_dummy          10884  0 
psmouse                45200  0 
pcspkr                 10624  0 
rfkill                 17176  2 iwl3945
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
mac80211              216820  1 iwl3945
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class              12164  1 iwl3945
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               32392  2 iwl3945,mac80211
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  19736  3 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
bluetooth              61924  11 rfcomm,bnep,sco,l2cap,btusb
fglrx                1813960  30 
container              11520  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
battery                18436  0 
ac                     12292  0 
button                 14224  0 
intel_agp              33724  0 
agpgart                42184  2 fglrx,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
ata_generic            12932  0 
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  0 
ahci                   37132  1 
pata_acpi              12160  0 
libata                177312  4 ata_generic,ata_piix,ahci,pata_acpi
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  5 btusb,usbhid,uhci_hcd,ehci_hcd
e1000e                112680  0 
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3
```

I'm using the iwl3945-driver, but I don't know which modules to load manually / write in a config file.

I want to know which modules I have to add to which config file.

Thank you.

---

