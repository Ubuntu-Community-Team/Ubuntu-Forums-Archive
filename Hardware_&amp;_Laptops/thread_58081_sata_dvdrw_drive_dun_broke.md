---
title: "sata dvdrw drive dun broke"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by sunscape on 2005-08-18
Basically I have a dvdrw drive attached to my motherboard's sata controller and it does not work. I get the following error during boot:

I/O resource 0x170 0x177 not free.
Ports already in use.

I thought this was fixed some time ago but it seems to still be a problem.

Does anyone know how to make it work?

The chipset is intel ich6.

Thank you!


Module                  Size  Used by
isofs                  36668  1
udf                    89412  0
proc_intf               4260  0
freq_table              4320  0
cpufreq_userspace       6240  0
cpufreq_ondemand        6728  0
cpufreq_powersave       1856  0
fglrx                 262440  7
video                  16196  0
sony_acpi               6152  0
pcc_acpi               11232  0
button                  6704  0
battery                10212  0
container               4544  0
ac                      4900  0
ipv6                  257760  405
sd_mod                 18080  0
sg                     38656  0
sr_mod                 17444  1
af_packet              22504  2
r8169                  20168  0
i2c_i801                8652  0
i2c_core               22720  1 i2c_i801
ata_piix                9412  0
libata                 49508  1 ata_piix
usb_storage            72288  1
scsi_mod              128224  5 sd_mod,sg,sr_mod,libata,usb_storage
tsdev                   7776  0
ehci_hcd               33252  0
usbhid                 32384  0
uhci_hcd               33488  0
usbcore               119480  5 usb_storage,ehci_hcd,usbhid,uhci_hcd
snd_azx                16576  1
snd_hda_codec          47168  1 snd_azx
snd_pcm_oss            54304  0
snd_mixer_oss          20320  2 snd_pcm_oss
snd_pcm                96772  3 snd_azx,snd_hda_codec,snd_pcm_oss
snd_timer              26532  1 snd_pcm
snd                    59876  6 snd_azx,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10400  2 snd
snd_page_alloc         10212  2 snd_azx,snd_pcm
shpchp                 99620  0
pci_hotplug            33980  1 shpchp
intel_agp              22396  1
agpgart                34284  1 intel_agp
pcspkr                  3788  0
rtc                    12776  0
evdev                   9600  0
md                     48112  0
dm_mod                 60480  1
capability              4872  0
commoncap               8032  1 capability
psmouse                21736  0
mousedev               11612  1
parport_pc             37924  1
lp                     11464  0
parport                37352  2 parport_pc,lp
ide_cd                 42052  0
cdrom                  40476  2 sr_mod,ide_cd
ext3                  138664  1
jbd                    63672  1 ext3
mbcache                 8452  1 ext3
ide_generic             1536  0
ide_disk               20896  4
ide_core              129656  4 usb_storage,ide_cd,ide_generic,ide_disk
unix                   28692  751
thermal                13672  0
processor              23400  1 thermal
fan                     4612  0
fbcon                  37856  0
font                    8416  1 fbcon
bitblit                 5696  1 fbcon
vesafb                  6948  0
cfbcopyarea             4032  1 vesafb
cfbimgblt               3136  1 vesafb
cfbfillrect             3712  1 vesafb

---

