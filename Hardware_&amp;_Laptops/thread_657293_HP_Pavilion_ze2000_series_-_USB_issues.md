---
title: "HP Pavilion ze2000 series - USB issues"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by Akira_Oni on 2008-01-03
I just bought an HP Pavilion model ze2008wm used, and installed Ubuntu linux on it. While, to my dismay alot of programs seem to be crashing, my only major concern is that my usb ports will not provide power to any devices. I'm not sure if it's a driver issue, or an incompatability with hardware. I did contact HP for the specs of the device, and I will provide them now.

**Product Name**    	 ze2008wm
**Microprocessor** 	1.3GHz Intel® Celeron® M Processor 350
**Microprocessor Cache** 	1MB L2 Cache
**Memory** 	256MB DDR SDRAM (1 x 256MB) at 266MHz
**Memory Max** 	1024MB DDR SDRAM (2 x 512MB)
**Video Graphic**s 	Intel® Extreme Graphics 2
**Video Memory** 	(shared) 64mb
**Hard Drive** 	40GB (4200RPM) Hard Drive
**Diskette Drive** 	External USB Floppy Drive available for customers via hpshopping.com or local retailers
**Multimedia Drive** 	24X DVD/CD-RW Combo Drive
**Display** 	15.0"XGA TFT (1024 x 768) display
**Fax/Modem** 	high speed 56k modem
**Network Card** 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
**Wireless Connectivity** 	54g™ 802.11b/g WLAN with 125HSM/SpeedBooster™ support
**Sound** 	16-bit Sound Blaster Pro-compatible audio; internal Harman/Kardon® speakers; AC audio link; volume control button and mute button
**Keyboard** 	101-key compatible
**Pointing Device** 	Touch Pad with dedicated vertical and horizontal Scroll up/down pad
**PC Card Slots** 	

    * 1 Type I/II 32-bit card bus (also supports 16-bit)

**External Ports** 	

    * 2 Universal Serial Bus (USB) 2.0
    * 1 headphone-out
    * 1 microphone-in
    * 1 VGA (15-pin)
    * 1 RJ-11 (modem)
    * 1 RJ -45 (LAN)
    * 1 IEEE1394(4-pin)

**Dimensions** 	13.15"(W) x 10.80"(L) x1.29"(min)/1.63"(max)(H)
**Weight** 	6.27lbs.(I)

**Power** 	

    * 65W AC adapter
    * 6-Cell Lithium-Ion battery

Does anyone know what steps I need take to get my usb ports powered on?

---

### Post by Yellow Pasque on 2008-01-03
Do an lsmod command and let's see if you have the proper modules for usb.
Look for lines like the following:
```
usbcore               170096  4 usbhid,ehci_hcd,ohci_hcd
hid                    36420  1 usbhid
```

Another good thing to check would be if the system recognizes your USB controllers. Look under System -> Preferences -> Hardware Info 
OR do the following commands and see if it lists any USB controllers:
```
sudo update-pciids
sudo lspci
```

---

### Post by Akira_Oni on 2008-01-03
I included the entire readout, since I didn't know what else you needed. However here is the usbcore data.

usbcore               138632  3 ehci_hcd,uhci_hcd

```
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  8 
af_packet              24840  2 
i915                   25856  2 
drm                    83348  3 i915
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
video                  18060  0 
sbs                    19592  0 
battery                11012  0 
container               5504  0 
dock                   10656  0 
ac                      6148  0 
button                  8976  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  3 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_pcm                80388  9 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
joydev                 11328  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcmcia                 41388  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
bcm43xx               127336  0 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    54660  25 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               8068  0 
psmouse                39952  0 
soundcore               8800  1 snd
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
8139too                27776  0 
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ata_piix               17540  3 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

---

### Post by Akira_Oni on 2008-01-05
Still got nothin. Link me to a solution or somethin plz.

---

### Post by Akira_Oni on 2008-01-07
Once again, I have tried the suggested commands with little success. Does anyone have a suggestion?

---

### Post by Yellow Pasque on 2008-01-07
I'm not sure if you saw this since I edited it in later, but could you do this for me and give the output of the lspci command?

> **Temüjin said:**
> Another good thing to check would be if the system recognizes your USB controllers. Look under System -> Preferences -> Hardware Info 
OR do the following commands and see if it lists any USB controllers:
```
sudo update-pciids
sudo lspci
```

---

### Post by Akira_Oni on 2008-01-10
I'm not exactly sure what you're looking for, so here's the final readout:

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
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
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller

```

---

### Post by Akira_Oni on 2008-01-22
Hello?

---

### Post by Akira_Oni on 2008-01-22
Does anyone have any suggestions? Because I'm stumped, I can't seem to find any drivers, and I don't know what to do. Could I use WINE to emulate the windows drivers?

---

### Post by ubuntu-freak on 2008-01-28
> **Akira_Oni said:**
> Does anyone have any suggestions? Because I'm stumped, I can't seem to find any drivers, and I don't know what to do. Could I use WINE to emulate the windows drivers?

 
You can't use Wine for that.
 
I tried doing a search in google but it seems you're the only person using that laptop with Ubuntu (or no one else is having issues, doubt it).
 
I have a very similar laptop to you. Mine is a HP Pavillion ze2000 and the only issue I have is that my battery meter doesn't work. We must have different motherboards, that's where your problems stem from I think.
 
Have you thought of trying Ubuntu Fiesty Fawn (or even Edgy), then wait and see how Hardy works? Or you could try pure Debian, supports older hardware better.
 
If you get things working better, give my multimedia and video how-to a go. 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

