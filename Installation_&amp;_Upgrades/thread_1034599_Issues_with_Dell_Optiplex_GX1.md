---
title: "Issues with Dell Optiplex GX1"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by raziel420 on 2009-01-08
Well I'm aware this qualifies and an antique system, but hey the price was right (free is good).  Now the problem is getting all the configuration kinks out of it (and I thought my other antique system was hard).  So video is not properly configured (I still see just fine, but I'd like to get it working right, maybe get a touch of compiz going), and the dreaded sound issues, so here be the info thats always asked for.

raziel@:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
raziel@:~$ lsmod
Module                  Size  Used by
ipv6                  263972  8 
binfmt_misc            16904  1 
af_packet              25728  2 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
container              11520  0 
wmi                    14504  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_opl3_lib           18560  0 
snd_hwdep              15236  1 snd_opl3_lib
snd_cs4236_lib         22784  0 
snd_mpu401_uart        15360  0 
snd_cs4231_lib         32640  1 snd_cs4236_lib
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_cs4236_lib,snd_cs4231_lib,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device         15116  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_cs4231_lib,snd_pcm
dcdbas                 15008  0 
evdev                  17696  5 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
serio_raw              13444  0 
psmouse                45200  0 
button                 14224  0 
i2c_piix4              16144  0 
i2c_core               31892  1 i2c_piix4
pcspkr                 10624  0 
intel_agp              33724  1 
isp1760                26400  0 
shpchp                 38036  0 
agpgart                42184  1 intel_agp
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_piix               24580  2 
ata_generic            12932  0 
uhci_hcd               30736  0 
libata                178208  3 pata_acpi,ata_piix,ata_generic
usbcore               149360  3 isp1760,uhci_hcd
3c59x                  48936  0 
mii                    13440  1 3c59x
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


The one thing not already on that list is the monitor, which is a phillips magnavox mv5011

---

