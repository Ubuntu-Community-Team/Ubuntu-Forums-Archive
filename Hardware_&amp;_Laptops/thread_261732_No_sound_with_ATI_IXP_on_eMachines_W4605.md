---
title: "No sound with ATI IXP on eMachines W4605"
date: 2006-09-20
forum: Hardware &amp; Laptops
---

### Post by HoneyGutClusters on 2006-09-20
Yep. The Wal-mart special...

The only thing holding me back from complete Ubuntu adoption is this. I've tried adding the noapic line in grub, I've compiled alsa 1.0.12 from source using the directions for ATIIXP on alsa's site, adding in sudo before make install, to no avail. I've ran alsaconf and checked to ensure that sound was not muted, but still nothing. I'm at a loss here...

Here's my module list as given by lsmod:
```

Module                  Size  Used by
ipv6                  265728  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  0
drm                    73236  1 radeon
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ndiswrapper           177364  0
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
af_packet              22920  8
snd_atiixp             19724  1
snd_ac97_codec         96804  1 snd_atiixp
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            47648  0
snd_mixer_oss          18816  1 snd_pcm_oss
snd_pcm                81032  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              24964  1 snd_pcm
snd                    56164  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
joydev                 10048  0
tsdev                   8000  0
soundcore              10208  1 snd
psmouse                36100  0
rtc                    13492  0
tg3                   101764  0
snd_page_alloc         10760  2 snd_atiixp,snd_pcm
serio_raw               7300  0
pcmcia                 40508  0
sdhci                  14848  0
mmc_core               30104  1 sdhci
pcspkr                  2180  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
ati_agp                 9100  0
agpgart                34888  2 drm,ati_agp
evdev                   9856  2
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130820  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  3
generic                 5124  0
atiixp                  6800  1
thermal                13576  0
processor              23360  2 powernow_k8,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```
Hopefully someone here knows what to do next, because I sure don't.]

---

### Post by HoneyGutClusters on 2006-09-25
Okay, I figured it out. Here's what you need to do:

Open a console, then run "alsamixer" (without the quotes). Use the right arrow to highlight IEC958, then hit the "m" key to mute it. tap escape twice to exit, then try your sound again.

---

