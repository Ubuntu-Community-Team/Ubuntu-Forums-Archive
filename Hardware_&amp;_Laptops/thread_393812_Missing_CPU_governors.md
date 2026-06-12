---
title: "Missing CPU governors"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by jhhoward on 2007-03-26
I recently read about how to make the gnome CPU scaling monitor applet control the frequency of the CPU. I originally was always kept at 'dynamic' which cut my processor cores down to 1.0GHz and fired up to 1.67GHz when needed. I had four CPU governors: Performance, Dynamic, Userspace and Powersave (Dynamic may have been 'ondemand' I can't quite remember)

I followed this post:
[http://www.ubuntuforums.org/showthread.php?t=76266](http://www.ubuntuforums.org/showthread.php?t=76266)
to let me change the governor that was being used. This let me select 'powersave' for when I was running on battery.

The problem is now that I only have the 'performance' governor, which sets my CPU to the highest frequency. I'm not sure what has caused this exactly.
If I open a console and type
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

I get:
performance

Any way to fix this?
Thanks,
James

---

### Post by s0cket on 2007-03-26
sudo lsmod and see if the modules for the governers are being loaded at startup.

---

### Post by jhhoward on 2007-03-28
I'm not exactly what I should be looking for but here is the output from lsmod:

```
Module                  Size  Used by
isofs                  38076  1 
udf                    89348  0 
vmnet                  41900  15 
vmmon                 118668  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
speedstep_centrino      9760  1 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
freq_table              6048  1 speedstep_centrino
af_packet              24584  2 
arc4                    3200  2 
ieee80211_crypt_wep     6528  1 
ipv6                  272288  14 
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
nls_iso8859_1           5248  1 
nls_cp437               6912  2 
vfat                   14720  1 
fat                    56348  1 vfat
nls_utf8                3200  1 
ntfs                  112116  1 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          19584  2 snd_pcm_oss
snd_seq_dummy           4996  0 
joydev                 11200  0 
pcmcia                 40380  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
tsdev                   9152  0 
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               6830836  22 
ipw3945               124576  1 
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
sr_mod                 18212  1 
cdrom                  38944  1 sr_mod
sg                     37404  0 
psmouse                41352  0 
sdhci                  20108  0 
mmc_core               32136  1 sdhci
tifm_7xx1               9472  0 
tifm_core              10496  1 tifm_7xx1
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
r1000                  17792  0 
evdev                  11392  2 
i2c_core               23424  2 i2c_ec,nvidia
serio_raw               8452  0 
ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211
irda                  214332  0 
intel_agp              26012  1 
agpgart                34888  2 nvidia,intel_agp
snd                    58372  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt               3200  1 irda
soundcore              11232  2 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142856  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
sd_mod                 22656  5 
generic                 6276  0 
ata_piix               11780  5 
libata                 74892  1 ata_piix
scsi_mod              144648  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
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

Just so it might be useful, my processor is an Intel Core Duo 1.66GHz

Thanks,
James

---

