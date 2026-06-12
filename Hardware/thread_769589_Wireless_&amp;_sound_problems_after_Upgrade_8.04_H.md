---
title: "Wireless &amp; sound problems after Upgrade 8.04 Hardy Heron"
date: 2008-04-26
forum: Hardware
---

### Post by manugap on 2008-04-26
Hello there,

I'm experiencing sound and wireless problems since my update from ubuntu 7.10 to ubuntu 8.04.

The sound is not working at all, and the wireless connection stops working after a while (although the try icon says the connectivity is ok).

Both of this services were working fine with the previous version.

My machine is an ASUS PRO31S mod F3SA laptop, running the standard 64 bit kernel:

```

$ uname -a
Linux rotor 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

```

Some more information:

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
08:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```


```

$ lsmod 
Module                  Size  Used by
af_packet              27272  0 
snd_rtctimer            5344  1 
binfmt_misc            14860  1 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
ppdev                  11400  0 
acpi_cpufreq           10832  2 
cpufreq_ondemand       11152  1 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_powersave       3200  0 
cpufreq_stats           8416  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
nls_iso8859_1           6656  2 
nls_cp437               8320  2 
vfat                   16256  2 
fat                    60592  1 vfat
ipv6                  311720  10 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9476  1 ecb
joydev                 15488  0 
hci_usb                19228  0 
bluetooth              67748  5 rfcomm,l2cap,hci_usb
snd_hda_intel         440408  5 
snd_hwdep              12552  1 snd_hda_intel
snd_pcm_oss            47648  0 
snd_pcm                92168  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_mixer_oss          20224  1 snd_pcm_oss
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
iwl3945               100468  0 
iwlwifi_mac80211      251876  1 iwl3945
uvcvideo               62084  0 
snd_seq_midi           10688  0 
fglrx                1804800  24 
video                  23444  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
atl1                   40460  0 
snd_rawmidi            29856  1 snd_seq_midi
cfg80211               17680  1 iwlwifi_mac80211
mii                     7552  1 atl1
output                  5632  1 video
serio_raw               9092  0 
ac                      8328  0 
battery                16776  0 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
psmouse                46236  0 
sdhci                  21508  0 
ricoh_mmc               5120  0 
mmc_core               59272  1 sdhci
snd_seq                63232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
asus_laptop            22492  0 
snd                    70856  22 snd_rtctimer,snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               7176  1 asus_laptop
intel_agp              30624  0 
iTCO_wdt               15312  0 
button                 10912  0 
soundcore              10400  1 snd
iTCO_vendor_support     5764  1 iTCO_wdt
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
evdev                  14976  6 
pcspkr                  4992  0 
ext3                  149264  2 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sg                     41880  0 
ata_piix               24196  0 
pata_acpi               9856  0 
sd_mod                 33280  7 
usbhid                 35168  0 
hid                    44992  1 usbhid
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
ata_generic             9988  0 
ahci                   33028  6 
libata                176304  4 ata_piix,pata_acpi,ata_generic,ahci
scsi_mod              178488  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               41996  0 
uhci_hcd               29856  0 
usbcore               169904  6 hci_usb,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              41448  4 acpi_cpufreq,thermal
fan                     6792  0 
fuse                   56112  3 
vesafb                 10504  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit

```

Any ideas?


thanks on advance

manu

---

### Post by Acutidens on 2008-09-07
I had the same problem with the sound (Intel ICH8 Southbridge = snd-hda-intel ALSA module).

Try adding this line at the end of the file /etc/modprobe.d/alsa-base:

```
options snd-hda-intel model=auto
```

See also this thread:

[ALSA 1.0.17 Installation Script]("http://ubuntuforums.org/showthread.php?t=820959")

---

