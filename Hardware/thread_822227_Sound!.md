---
title: "Sound?!"
date: 2008-06-08
forum: Hardware
---

### Post by lamborghinipro on 2008-06-08
Hi, I know this is such a common problem, but I have tried everything and can't get it my sound to work. The only sounds I hear is the opening Ubuntu sound. No software sounds, Firefox, Pidgin, etc. 

LSMOD RESULTS:

```
Module                  Size  Used by
snd_rtctimer            4640  0 
ipx                    29348  0 
p8023                   3072  1 ipx
r8169                  32900  0 
ipv6                  267780  12 
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  11 
usblp                  15872  0 
snd_intel8x0           35356  5 
snd_seq_dummy           4868  0 
snd_ens1371            27168  22 
nvidia               7825536  34 
gameport               16008  1 snd_ens1371
snd_ac97_codec        101028  2 snd_intel8x0,snd_ens1371
snd_seq_oss            35584  0 
ac97_bus                3072  1 snd_ac97_codec
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_ens1371,snd_seq_midi
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
i2c_core               24832  1 nvidia
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_pcm                78596  11 snd_intel8x0,snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0 
snd_timer              24836  10 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    56996  53 snd_rtctimer,snd_intel8x0,snd_seq_dummy,snd_ens1371,snd_ac97_codec,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
usb_storage            73664  0 
ext2                   73352  1 
mbcache                 9600  1 ext2
usbhid                 31872  0 
libusual               19108  1 usb_storage
hid                    38784  1 usbhid
sg                     36880  0 
sd_mod                 30720  3 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
ata_piix               19588  3 
pata_acpi               8320  0 
floppy                 59588  0 
ata_generic             8324  0 
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  5 usb_storage,sg,sd_mod,sr_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 usblp,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

Please help me, I have Realtek AC'97 audio (for Windows, anyway) because it is an integrated sound card. I tried installing Realtek's linux driver and it didnt change anything, so please help! I need sound!

---

### Post by Nepherte on 2008-06-08
What's the result of the aplay -l and lspci command?

---

### Post by lamborghinipro on 2008-06-08
```
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH7 [Intel ICH7], device 4: Intel ICH - IEC958 [Intel ICH7 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)
02:00.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

---

### Post by Nepherte on 2008-06-08
You have two sound cards? If so, try disabling one of them (for example the on board card, in the bios).

---

### Post by lamborghinipro on 2008-06-08
hmmm....

---

