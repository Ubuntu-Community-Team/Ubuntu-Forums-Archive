---
title: "Laptop not fully shut down"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by blumf on 2008-01-30
Laptop : Toshiba Equium A200 - 1V0
Ubuntu : 7.10

I've noticed that my laptop drains 10-20% power from the battery overnight despite being shut down from Ubuntu. If I shut down from Vista (dual-boot install) the battery is full the next day.

The laptop appears to shut down properly from Ubuntu, percent bar count down, screen goes off, no lights, no disk/fan sound. But, presumably, it's only being put into some sleep state rather than fully off.

In case it's any help...

lsmod:
```
Module                  Size  Used by
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
button                  8976  0 
ac                      6148  0 
container               5504  0 
sbs                    19592  0 
dock                   10656  0 
video                  18060  0 
battery                11012  0 
ipv6                  273892  12 
af_packet              24840  2 
r8187                  56200  0 
ieee80211_rtl          67076  1 r8187
ieee80211_crypt_ccmp_rtl     8448  0 
ieee80211_crypt_tkip_rtl    11648  0 
ieee80211_crypt_wep_rtl     6272  0 
ieee80211_crypt_rtl     6788  4 ieee80211_rtl,ieee80211_crypt_ccmp_rtl,ieee80211_crypt_tkip_rtl,ieee80211_crypt_wep_rtl
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sky2                   46852  0 
xpad                    9988  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              25620  1 
serio_raw               8068  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
agpgart                35016  3 drm,intel_agp
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
joydev                 11328  0 
evdev                  11136  7 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sg                     36764  0 
sd_mod                 30336  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_piix               17540  0 
ehci_hcd               36492  0 
ata_generic             8452  0 
ahci                   23300  4 
libata                125168  3 ata_piix,ata_generic,ahci
scsi_mod              147084  4 sr_mod,sg,sd_mod,libata
uhci_hcd               26640  0 
usbcore               138632  6 r8187,xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

```

---

### Post by cdtech on 2008-01-30
That sounds weird. But I myself have noticed the same with my battery. I think its a charge issue in Ubuntu and not a power drain overnight. Pull your battery after shutdown and in the morning see if you have the same issues.

Right now mine shows fully charged but if I leave for a bit and power up the charge light comes on and the battery indicator shows not fully charged, maybe 94%.

I'll try the battery thing tonight and see what mine does.

---

### Post by blumf on 2008-01-30
Nope, that's not the issue, the laptop retains it's charge if I shut down from Windows. Although I did try leaving the battery out one night and it kept it's charge as you'd expect.

---

### Post by cdtech on 2008-01-30
If you would shut down, with a fully charged battery, in Ubuntu and reboot into windows, what would the battery level indicate?

The ram is nonvolatile and the bios uses its own battery to retain its memory.

hmmm.... I'm going to try a few things. This is interesting.

---

### Post by blumf on 2008-01-31
Last night I tried using the 8.04 Alpha 3 install disk to shutdown with, on the off-chance that a newer ACPI or something else might help. Same result though, battery drain overnight.

---

### Post by Mean-Machine on 2008-05-13
I've got the same laptop, unfortunately the same 'battery drain overnight' problem also occurs.

Has anyone found a solution, or at least a reason for it yet?

---

