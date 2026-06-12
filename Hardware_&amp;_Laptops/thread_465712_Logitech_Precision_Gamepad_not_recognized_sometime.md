---
title: "Logitech Precision Gamepad not recognized sometimes"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by punkrockscks on 2007-06-06
Just bought a Logitech Precision USB gamepad to use with my brand new Feisty based MythTv box I made.  Everything is great, except the game pad isn't recognized by gfce ultra or zsnes or mame with the MythTv user, but works fine under the other user account I made.  Heres lsusb and lsmod from the "Mythtv" user, if they help.


```
lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 1241:1166 Belkin 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0b38:0003  
Bus 002 Device 004: ID 046d:c21a Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

```
$ lsmod
Module                  Size  Used by
isofs                  36284  1 
udf                    85252  0 
binfmt_misc            12680  1 
i915                   24448  3 
drm                    81044  4 i915
speedstep_lib           6148  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
asus_acpi              17308  0 
dock                   10268  0 
video                  16388  0 
battery                10756  0 
ac                      6020  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
backlight               7040  1 asus_acpi
button                  8720  0 
ipv6                  268704  12 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  2 parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0 
psmouse                38920  0 
serio_raw               7940  0 
pcspkr                  4224  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
intel_agp              25116  1 
agpgart                35400  3 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
joydev                 10816  0 
tsdev                   8768  0 
evdev                  11008  4 
usbhid                 26592  0 
hid                    27392  1 usbhid
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
ata_piix               15492  3 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sd_mod,sr_mod,libata
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 xpad,usbhid,ehci_hcd,uhci_hcd
e1000                 126016  0 
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
```

---

### Post by Hells_Dark on 2008-05-31
Up

---

