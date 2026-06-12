---
title: "kernel trouble, SMP and onboard Promise RAID"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by Centx on 2006-08-22
Im trying to get both my processors working, using ubuntu 6.06, Ive tried both installing SMP kernel from the repos and homebrewed from kernel.org.
with the one from the repos, my computer freezes after boot, at the gdm loginscreen, and the vanilla one doesnt recognise my three main HDD's (or so it seems at least, since I get a device busy message trying to mount them, even though they are not mounted).
It seems like there is some modules not loaded when I use the vanilla kernel, unfortunatly, I dont know how to activate them in the .config

please just ask for more info if there is anything crucial I havent mentioned.

more info

(lsmod) with the standard ubuntu 6.15 kernel:

Module                  Size  Used by
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0 
speedstep_lib           4484  0 
cpufreq_userspace       4696  0 
cpufreq_stats           5636  0 
freq_table              4740  1 cpufreq_stats
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
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
nls_iso8859_1           4224  1 
nls_cp437               5888  1 
vfat                   13440  1 
fat                    53020  1 vfat
ipv6                  265728  6 
dm_mod                 58936  1 
md_mod                 72532  0 
af_packet              22920  2 
sbp2                   24196  0 
lp                     11844  0 
snd_cmipci             34336  0 
snd_opl3_lib           10624  1 snd_cmipci
snd_hwdep               9376  1 snd_opl3_lib
tsdev                   8000  0 
usb_storage            74176  1 
usbhid                 39904  0 
e1000                 118840  0 
analog                 12320  0 
gameport               15496  2 snd_cmipci,analog
nvidia               4550772  0 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
i2c_core               21904  2 i2c_acpi_ec,nvidia
snd_intel8x0           33692  1 
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
floppy                 62148  0 
snd_mpu401              6728  0 
snd_mpu401_uart         7808  2 snd_cmipci,snd_mpu401
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
hw_random               5652  0 
pcspkr                  2180  0 
rtc                    13492  0 
psmouse                36100  0 
serio_raw               7300  0 
snd_timer              25220  2 snd_opl3_lib,snd_pcm
snd                    55268  15 snd_cmipci,snd_opl3_lib,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
intel_agp              22940  1 
agpgart                34888  2 nvidia,intel_agp
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
evdev                   9856  1 
sg                     37920  0 
ext3                  135688  5 
jbd                    58772  1 ext3
ide_generic             1536  0 
ohci1394               35124  0 
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0 
uhci_hcd               33680  0 
usbcore               130692  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
sr_mod                 16932  0 
cdrom                  38560  1 sr_mod
generic                 5124  0 
ata_piix               11012  10 
sd_mod                 19984  11 
sata_promise           11780  2 
libata                 78992  2 ata_piix,sata_promise
scsi_mod              139496  7 sbp2,usb_storage,sg,sr_mod,sd_mod,sata_promise,libata
thermal                13576  0 
processor              23360  1 thermal
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




with the one from kernel.org:
 
Module                  Size  Used by
rfcomm                 39828  0 
l2cap                  26112  5 rfcomm
bluetooth              51556  4 rfcomm,l2cap
ppdev                  10372  0 
ipv6                  261504  14 
speedstep_lib           5764  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7208  0 
freq_table              5792  1 cpufreq_stats
cpufreq_powersave       2816  0 
cpufreq_ondemand        8364  0 
cpufreq_conservative     8200  0 
video                  16260  0 
button                  7568  0 
battery                10372  0 
container               5376  0 
ac                      5764  0 
dm_mod                 57108  1 
md_mod                 79636  0 
af_packet              23944  2 
sbp2                   23816  0 
lp                     12928  0 
snd_cmipci             34976  1 
snd_opl3_lib           11520  1 snd_cmipci
snd_intel8x0           33820  0 
snd_ac97_codec         94112  1 snd_intel8x0
snd_hwdep              10244  1 snd_opl3_lib
snd_ac97_bus            3328  1 snd_ac97_codec
snd_mpu401_uart         9216  1 snd_cmipci
snd_pcm_oss            42144  0 
snd_mixer_oss          18944  1 snd_pcm_oss
tsdev                   8896  0 
snd_pcm                86148  4 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            25760  1 snd_mpu401_uart
snd_seq_device          9100  2 snd_opl3_lib,snd_rawmidi
snd_timer              24452  2 snd_opl3_lib,snd_pcm
analog                 12960  0 
intel_agp              24604  1 
e1000                 113976  0 
parport_pc             36720  1 
hw_random               6936  0 
snd                    54496  14 snd_cmipci,snd_opl3_lib,snd_intel8x0,snd_ac97_codec,snd_hwdep,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq_device,snd_timer
floppy                 61812  0 
gameport               16520  2 snd_cmipci,analog
soundcore              10976  1 snd
parport                38856  3 ppdev,lp,parport_pc
rtc                    14644  0 
pcspkr                  4096  0 
agpgart                33868  1 intel_agp
psmouse                40328  0 
serio_raw               7940  0 
snd_page_alloc         11016  2 snd_intel8x0,snd_pcm
shpchp                 41000  0 
pci_hotplug            32068  1 shpchp
evdev                  11008  1 
sr_mod                 17316  0 
sg                     35740  0 
cdrom                  38192  1 sr_mod
ide_generic             2304  0 [permanent]
ohci1394               36016  0 
ieee1394              298968  2 sbp2,ohci1394
uhci_hcd               23820  0 
ehci_hcd               33160  0 
usbcore               128540  3 uhci_hcd,ehci_hcd
generic                 5380  0 [permanent]
ata_piix               13316  5 
sd_mod                 22016  9 
sata_promise           12676  3 
libata                 70412  2 ata_piix,sata_promise
scsi_mod              135660  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                14216  0 
processor              24424  1 thermal
fan                     5636  0 
vga16fb                13576  0 
cfbcopyarea             4736  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               3968  1 vga16fb
cfbfillrect             4992  1 vga16fb

---

