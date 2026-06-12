---
title: "Apiotek Express card eSata II 300 working??"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by rosagonzpe on 2008-01-25
First of all forgive my english if I commit any errors, It is not my first language, and thanks in advance!

After doing some useless googling, and trying to make it work, I bring the issue here:

Does anyone have this device working?

THE PROBLEM:
I am not able to "switch it on" the card, and I would like to use my external esata drive. The Express Card controller seems to be recognized, but not the device (the actual apiotek card).

GATHERED DATA:

  - DEVICE: Apiotek Express card eSata II 300

  -LSPCI:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)

  - LSMOD:

Module                  Size  Used by
ipv6                  273892  10 
wlan_tkip              13696  3 
af_packet              24840  4 
snd_rtctimer            4384  1 
hci_usb                18332  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  7 hci_usb,rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
button                  8976  0 
container               5504  0 
video                  18060  8 
dock                   10656  0 
sbs                    19592  0 
ac                      6148  0 
battery                11012  0 
applesmc               18432  0 
led_class               5380  1 applesmc
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
nvidia               6221648  26 
snd_rawmidi            25728  1 snd_seq_midi
uvcvideo               48644  0 
joydev                 11328  0 
i2c_core               26112  1 nvidia
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          2304  1 uvcvideo
wlan_scan_sta          15232  1 
xpad                    9988  0 
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
sky2                   46852  0 
ath_rate_sample        14976  1 
appletouch             10880  0 
ath_pci               164144  0 
wlan                  237392  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               233952  3 ath_rate_sample,ath_pci
snd                    54660  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34580  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
pci_hotplug            32704  1 shpchp
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
evdev                  11136  10 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_piix               17540  3 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sd_mod,sr_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 hci_usb,uvcvideo,xpad,appletouch,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


Anyone has any ideas??
I think that the express card device in my computer it is working, what I probably need are drivers for the card. Am I right?

Thanks in advance!

---

