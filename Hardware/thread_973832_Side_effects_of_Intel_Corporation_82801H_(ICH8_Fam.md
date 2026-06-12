---
title: "Side effects of Intel Corporation 82801H (ICH8 Family)"
date: 2008-11-07
forum: Hardware
---

### Post by artpol84 on 2008-11-07
I have problem with sound card.
For some reason sound stops playing when i switch to console (Ctrl+Alt+F1[2,...]). On my previous laptop I have no such effect. Is this problem of Sound card driver or mixer?
And another side effect: sometimes i start Banshee (audio player) and there is no sound. If I close Firefox (on some pages with Ajax it plays sounds) and restart Banshee - all is ok. Seems like Firefox blocks sound card for other applications. I have no problem running concurrently Totem and Banshee.

Ubuntu version: 8.04
Kernel ver:
```
uname -a
Linux laptop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

```
PCI devices
```
lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

Loaded kernel modules:
```
 lsmod
Module                  Size  Used by
cdc_acm                17056  0 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
vboxdrv                61360  0 
ppdev                  10372  0 
ipv6                  267780  14 
acpi_cpufreq           10796  2 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
iwl3945                89844  0 
iwlwifi_mac80211      218980  1 iwl3945
snd_hda_intel         344856  5 
battery                14212  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
cfg80211               15112  1 iwlwifi_mac80211
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
video                  19856  0 
output                  4736  1 video
snd_rawmidi            25760  1 snd_seq_midi
serio_raw               7940  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
snd                    56996  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
intel_agp              25492  1 
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  3 drm,intel_agp
pcspkr                  4224  0 
evdev                  13056  7 
psmouse                40336  0 
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sg                     36880  0 
sd_mod                 30720  5 
ata_piix               19588  0 
pata_acpi               8320  0 
ahci                   28548  4 
ata_generic             8324  0 
libata                159344  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
r8169                  33156  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  4 cdc_acm,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

---

### Post by kostkon on 2008-11-07
I don't know about the console problem.

But for the *Flash* problem I assume that you have *Flash 9*. This version of *Flash* does not work well with *PulseAudio*, that's why you have this problem. You could install the *libflashsupport* package and make *Flash 9* work with *PulseAudio*, but in most cases this makes *Firefox* to crash a lot.

The best solution is to install *Flash 10*. You can download it from *Adobe*'s site. *Adobe* offers a deb package for 8.04

Before installing *Flash 10* you should completely remove *Flash 9*. To do this, open *Synaptic*, search for the *flashplugin-nonfree* package, left-click on it and select the *Complete Removal* option. Then, hit the *Apply* button to remove it. After doing this, close *Synaptic*.

Then just double click on the deb file of *Flash 10* that you have downloaded to install it.

---

