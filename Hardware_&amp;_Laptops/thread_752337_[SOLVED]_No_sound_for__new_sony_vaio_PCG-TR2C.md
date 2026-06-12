---
title: "[SOLVED] No sound for  new sony vaio PCG-TR2C"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by bigbrovar on 2008-04-11
The system is for my window fan friend whom i convinced to give ubuntu a try .. so i helped him install xubuntu .. everything worked like  a charm except his webcam and sound.. for now sound is his biggest issue and i would be happy if anyone can help me with tips on how to make sound work on this system.... 

on windows device manager claims the sound driver is Sound Max intergrated Digital Audio controller .. but when i did 

aplay -l on terminal i got this 

[PHP]**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [Intel 82801DB-ICH4 Modem], device 0: Intel ICH - Modem [Intel 82801DB-ICH4 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
[/PHP] 

xubuntu really rocks on this pc pls help so that it stays linux :lolflag:

---

### Post by bigbrovar on 2008-04-11
when i ran lspci in terminal i got this as the audio controller

 Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

i any idea on how i can make this work with linux

---

### Post by prshah on 2008-04-11
> **bigbrovar said:**
> 
xubuntu really rocks on this pc pls help so that it stays linux :lolflag:

A posting of the outputs of ```
lsmod
lspci

``` would help us help you help your friend! :)

---

### Post by bigbrovar on 2008-04-11
**_lsmod_**

[PHP]Module                  Size  Used by
i915                   25856  1 
drm                    83348  2 i915
sony_laptop            32088  0 
sonypi                 23960  0 
ppdev                  10244  0 
snd_atiixp_modem       17544  0 
snd_via82xx_modem      16392  0 
snd_intel8x0m          18956  5 
speedstep_centrino      8256  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
video                  18060  0 
battery                11012  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
container               5504  0 
sbs                    19592  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
snd_intel8x0           35356  1 
snd_ac97_codec        101668  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            43136  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 41388  0 
snd_seq_dummy           4868  0 
snd_seq_oss            34944  0 
joydev                 11328  0 
snd_seq_midi            9600  0 
ipw2100                72240  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
ieee80211              35656  1 ipw2100
ieee80211_crypt         7040  1 ieee80211
snd_seq                54000  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56068  24 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
ipv6                  273892  8 
evdev                  11136  8 
usb_storage            73024  0 
ide_core              116804  1 usb_storage
usbhid                 29536  0 
hid                    28928  1 usbhid
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
libusual               18448  1 usb_storage
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  2 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
e100                   37644  0 
mii                     6528  1 e100
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  6 usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
ay@ay-pc:~$ 
[/PHP]

**_lspci_**

[PHP]00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
[/PHP]

---

### Post by nnamdi on 2008-04-11
hey you try out this link probably should work for you
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by bigbrovar on 2008-04-11
i tried it but still no go

---

### Post by bigbrovar on 2008-04-11
thanks it works now .. i had to turn off external  app from alsa mixer ..

---

