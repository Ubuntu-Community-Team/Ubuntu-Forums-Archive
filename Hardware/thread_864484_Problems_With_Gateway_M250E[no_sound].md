---
title: "Problems With Gateway M250E[no sound]"
date: 2008-07-19
forum: Hardware
---

### Post by pr0blem on 2008-07-19
Hi everyone!

I have my new laptop with (x)ubuntu, but i have some problems with my sound card.

I'll try to install alsa(satisfactory) and all this.. but this dont work.

Here is my 'lspci' :
> ```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:07.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:09.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
```

And.. 'lspci | grep audio ':

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
```

lsmod :
```

Module                  Size  Used by
af_packet              23812  4 
ipv6                  267780  8 
i915                   32512  2 
drm                    82580  3 i915
vmnet                  38204  6 
vmmon                1824812  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
vboxdrv                61360  0 
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
tifm_sd                12936  0 
pcmcia                 40876  0 
evdev                  13056  7 
psmouse                40336  0 
serio_raw               7940  0 
ipw2200               146120  0 
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
video                  19856  0 
output                  4736  1 video
sdhci                  19076  0 
mmc_core               51460  2 tifm_sd,sdhci
tifm_7xx1               8576  0 
tifm_core              11012  2 tifm_sd,tifm_7xx1
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
battery                14212  0 
ac                      6916  0 
button                  9232  0 
pcspkr                  4224  0 
snd_intel8x0m          18956  5 
snd_intel8x0           35356  2 
snd_ac97_codec        101028  2 snd_intel8x0m,snd_intel8x0
shpchp                 34452  0 
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ac97_bus                3072  1 snd_ac97_codec
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_pcm                78596  5 snd_intel8x0m,snd_intel8x0,snd_ac97_codec
snd_timer              24836  1 snd_pcm
snd                    56996  17 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_intel8x0m,snd_intel8x0,snd_pcm
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  3 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
tg3                   116228  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1
```

lsmod | grep snd

```
snd_intel8x0m          18956  5 
snd_intel8x0           35356  2 
snd_ac97_codec        101028  2 snd_intel8x0m,snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm                78596  5 snd_intel8x0m,snd_intel8x0,snd_ac97_codec
snd_timer              24836  1 snd_pcm
snd                    56996  17 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_intel8x0m,snd_intel8x0,snd_pcm
```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [Intel ICH6 Modem], device 0: Intel ICH - Modem [Intel ICH6 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

I have alsa already configured(with alsaconf command) and the audio still dont work. (using intel8x0 or something like that)

Well, if somebody knows how help me thanks!!!

PD: I dont have any sound.

sudo dmesg | grep intel
```

[   33.731042] intel8x0_measure_ac97_clock: measured 54012 usecs
[   33.731048] intel8x0: clocking to 48000
[   33.775008] intel_rng: FWH not detected
[   37.102741] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
```

thanks for read!!!

---

### Post by pr0blem on 2008-07-19
no one knows? =/

---

### Post by mojo on 2009-01-05
Hi there, I am using IBM Thinkpad X41 with exactly same chipset and YES my sound stop working after few days running even though the sound module is indicated loaded and running. I was trying to ask for help but people from #xubuntu has no idea why it happened. The best way is to reinstall the whole distro and hope it won't happen again.

---

