---
title: "Toshiba laptop fan problem (Tecra M3)"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by jj9000 on 2007-01-13
Hi,

I'm running Dapper Drake (6.06) on a toshiba tecra m3.
The problem? **The fan turns on shortly after bootup, and does not turn off.**

```
rachel@rach:/$ uname -a
Linux rach 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux

```
ACPI kernel modules loaded:
```
rachel@rach:/$ lsmod | grep acpi
toshiba_acpi           10940  0
sony_acpi               5644  0
pcc_acpi               12416  0
dev_acpi               11140  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  2 i2c_acpi_ec,nvidia

```
All kernel modules:
```
rachel@rach:/$ lsmod
Module                  Size  Used by
arc4                    2048  2
ieee80211_crypt_wep     5120  1
af_packet              22920  4
ipv6                  265856  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
toshiba_acpi           10940  0
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
dm_mod                 58936  1
md_mod                 72532  0
sbp2                   24196  0
lp                     11844  0
pcmcia                 40508  0
joydev                 10048  0
sdhci                  14848  0
mmc_core               30104  1 sdhci
ipw2200               107308  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
tsdev                   8000  0
tpm_infineon            8468  0
tpm                    10784  1 tpm_infineon
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
parport_pc             35780  0
parport                36296  3 ppdev,lp,parport_pc
serio_raw               7300  0
psmouse                36100  0
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
pcspkr                  2180  0
hw_random               5652  0
rtc                    13492  0
sk98lin               201812  0
sky2                   39940  0
usbhid                 39904  0
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
nvidia               4551028  0
i2c_core               21904  2 i2c_acpi_ec,nvidia
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sr_mod                 16932  0
sg                     37920  0
evdev                   9856  4
cdrom                  38560  1 sr_mod
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 19984  3
generic                 5124  0
ata_piix               11012  6
ahci                   17284  0
libata                 78992  2 ata_piix,ahci
scsi_mod              139496  6 sbp2,sr_mod,sg,sd_mod,ahci,libata
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
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
rachel@rach:/$ lsmod | grep acpi
toshiba_acpi           10940  0
sony_acpi               5644  0
pcc_acpi               12416  0
dev_acpi               11140  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  2 i2c_acpi_ec,nvidia
rachel@rach:/$ lsmod
Module                  Size  Used by
arc4                    2048  2
ieee80211_crypt_wep     5120  1
af_packet              22920  4
ipv6                  265856  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
toshiba_acpi           10940  0
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
dm_mod                 58936  1
md_mod                 72532  0
sbp2                   24196  0
lp                     11844  0
pcmcia                 40508  0
joydev                 10048  0
sdhci                  14848  0
mmc_core               30104  1 sdhci
ipw2200               107308  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
tsdev                   8000  0
tpm_infineon            8468  0
tpm                    10784  1 tpm_infineon
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
parport_pc             35780  0
parport                36296  3 ppdev,lp,parport_pc
serio_raw               7300  0
psmouse                36100  0
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
pcspkr                  2180  0
hw_random               5652  0
rtc                    13492  0
sk98lin               201812  0
sky2                   39940  0
usbhid                 39904  0
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
nvidia               4551028  0
i2c_core               21904  2 i2c_acpi_ec,nvidia
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sr_mod                 16932  0
sg                     37920  0
evdev                   9856  4
cdrom                  38560  1 sr_mod
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 19984  3
generic                 5124  0
ata_piix               11012  6
ahci                   17284  0
libata                 78992  2 ata_piix,ahci
scsi_mod              139496  6 sbp2,sr_mod,sg,sd_mod,ahci,libata
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
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


I've read [http://ubuntuforums.org/showthread.php?t=302123](http://ubuntuforums.org/showthread.php?t=302123) , which seems to be pretty similar to my situation.

Unlike that poster, I have no temperature problems:
```
rachel@rach:/$ acpi -V
     Thermal 1: ok, 55.0 degrees C
  AC Adapter 1: on-line

```

I have tried **toshutils** from Jonathan Buzzard: [http://buzzard.me.uk/toshiba/index.html](http://buzzard.me.uk/toshiba/index.html) , since I would even be OK with manually controlling the fan. But here is what I get: 

```
rachel@rach:/$ fan
fan: laptop does not have cooling fan or kernel module not installed.

```

Toshset is supposed to do similar stuff, without the need of a kernel module (i think?) But I get: 
```
root@rach:/# toshset -v -q

 machine id: 0xfcff    BIOS version: 1.30    SCI version: 87.132
 toshset version: 1.71                  Toshiba Model: Portege M100/M300 Tecra M2/A2/A3
error when querying feature: battery save mode: FAILURE
error when querying feature: power source: FAILURE
error when querying feature: LCD backlight: FAILURE
error when querying feature: fan: FAILURE
error when querying feature: select bay: FAILURE
error when querying feature: select bay lock: FAILURE
error when querying feature: IR port: FAILURE
error when querying feature: USB legacy mode: FAILURE
error when querying feature: USB FDD emulation mode: FAILURE
error when querying feature: LAN controller: FAILURE
error when querying feature: sound logo: FAILURE
error when querying feature: startup logo: FAILURE
error when querying feature: Video out: FAILURE
error when querying feature: HibInfo: BIOS size: FAILURE
error when querying feature: HibInfo: memory size: FAILURE
error when querying feature: HibInfo: VRAM size: FAILURE
error when querying feature: Hibernation LBA: FAILURE
error when querying feature: flat panel: FAILURE
error when querying feature: system beep: FAILURE
error when querying feature: lcd brightness: FAILURE
error when querying feature: lcd intensity: FAILURE
error when querying feature: CPU speed: FAILURE
error when querying feature: CPU sleep mode: FAILURE
error when querying feature: Display stretch: FAILURE
error when querying feature: CPU cache: FAILURE
error when querying feature: cache policy: FAILURE
error when querying feature: speaker volume: FAILURE
error when querying feature: battery alarm: FAILURE
error when querying feature: panel alarm: FAILURE
error when querying feature: panel power: FAILURE
error when querying feature: hard disk auto-off time: FAILURE
error when querying feature: display auto-off time: FAILURE
error when querying feature: power-up mode: FAILURE
error when querying feature: battery percent: FAILURE
error when querying feature: second battery: FAILURE
error when querying feature: cooling method: FAILURE
error when querying feature: power-up alarm: FAILURE
error when querying feature: auto-off time: FAILURE
error when querying feature: parallel port mode: FAILURE
error when querying feature: Standby time: FAILURE
error when querying feature: Hibernation: FAILURE
error when querying feature: Pointer: FAILURE
error when querying feature: boot method: FAILURE
error when querying feature: wireless support: FAILURE
error when querying feature: wireless switch: FAILURE
error when querying feature: bluetooth: FAILURE
error when querying feature: user password: FAILURE
error when querying feature: supervisor password: FAILURE
error when querying feature: owner string: FAILURE
 HCI/SCI access mode: kernel
toshset: this computer is not supported

```



[SIZE="5"]
Any help would be greatly appreciated! This problem makes Ubuntu unusable on my laptop, and I don't want to go back to windows! ](*,)[/SIZE]

---

### Post by tweedledee on 2007-01-13
> **jj9000 said:**
> Hi,

I'm running Dapper Drake (6.06) on a toshiba tecra m3.
The problem? **The fan turns on shortly after bootup, and does not turn off.**


Try this thread: [http://www.ubuntuforums.org/showthread.php?t=330917](http://www.ubuntuforums.org/showthread.php?t=330917)

---

