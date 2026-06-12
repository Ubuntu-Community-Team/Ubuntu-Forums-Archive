---
title: "No Audio - nVidia mcp51 alc883"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by renzokuken on 2007-02-02
hi,

i havent been able to get my sound working on my laptop (Evesham A240 / Clevo M665JE).

I have checked all the settings in alsamixer to no avail. My sound card appears to be recognised, and audio files play without trouble in various players, i just cant hear anything. nothing is muted or turned down.

```
rob@nibelheim:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and

```

rob@nibelheim:~$ lsmod
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
powernow_k8            15008  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
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
nls_utf8                3200  1 
ntfs                  112116  1 
ipv6                  272288  10 
ndiswrapper           208656  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
joydev                 11200  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
tsdev                   9152  0 
pcmcia                 40380  0 
sg                     37404  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
af_packet              24584  4 
tifm_7xx1               9472  0 
nvidia               6830868  22 
sdhci                  20108  0 
tifm_core              10496  1 tifm_7xx1
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
agpgart                34888  1 nvidia
mmc_core               32136  1 sdhci
soundcore              11232  1 snd
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                41352  0 
evdev                  11392  1 
pcspkr                  4352  0 
serio_raw               8452  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
i2c_core               23424  2 i2c_ec,nvidia
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
forcedeth              32268  0 
ohci1394               37040  0 
ehci_hcd               34696  0 
ieee1394              306104  2 sbp2,ohci1394
ohci_hcd               22532  0 
usbcore               134912  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
generic                 6276  0 
sd_mod                 22656  4 
amd74xx                15260  0 [permanent]
sata_nv                11268  3 
libata                 74892  1 sata_nv
scsi_mod              144648  4 sbp2,sg,sd_mod,libata
thermal                15624  0 
processor              31560  2 powernow_k8,thermal
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


has anybody got this chipset working or know how i might go about fixing it? its the last thing not working on this laptop, all other issues have been resolved.

thanks

---

### Post by renzokuken on 2007-02-04
UPDATE : PROBLEM SOLVED

I compiled the latest alsa-driver from source (version 1.14rc2), rebooted and it worked perfectly.

this is the last issue i had on my laptop, i now have a fully working ubuntu laptop.

woohoo

---

