---
title: "Sound issues with Gutsy on Toshiba Satellite A70"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by Strangerdave on 2007-11-14
So I have installed Gutsy on my A70 Laptop and just after I log in, I hear the Ubuntu music play, however it cuts out once the gnome desktop loads up.

I am not sure why.

I use xmms to listen to mp3s and when I click on "play" I get a notice that it can not open audio.

Here is my lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:

```

I figured that the drivers must be installed since I hear music in the beginning.

Here is my lsmod:
```
Module                  Size  Used by
wlan_tkip              13696  2 
af_packet              24840  4 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ipv6                  273892  10 
ppdev                  10244  0 
acpi_cpufreq           10568  0 
speedstep_lib           6404  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
battery                11012  0 
button                  8976  0 
ac                      6148  0 
video                  18060  0 
dock                   10656  0 
container               5504  0 
sbs                    19592  0 
sbp2                   24072  0 
lp                     12580  0 
snd_atiixp_modem       17160  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_atiixp             21132  3 
snd_ac97_codec        100644  2 snd_atiixp_modem,snd_atiixp
snd_rawmidi            25728  1 snd_seq_midi
irda                  202300  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
joydev                 11328  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
wlan_scan_sta          15104  1 
pcmcia                 41388  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_rate_sample        14208  1 
ath_pci                98336  0 
sdhci                  18828  0 
snd_pcm                80388  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              24324  3 snd_seq,snd_pcm
crc_ccitt               3072  1 irda
mmc_core               28420  1 sdhci
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
serio_raw               8068  0 
psmouse                39952  0 
snd                    54660  15 snd_atiixp_modem,snd_seq_oss,snd_atiixp,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_atiixp_modem,snd_atiixp,snd_pcm
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
wlan                  206660  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192720  3 ath_rate_sample,ath_pci
i2c_piix4               9740  0 
ati_agp                10124  1 
agpgart                35016  2 drm,ati_agp
i2c_core               26112  1 i2c_piix4
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
8139cp                 25088  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
atiixp                  7056  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,atiixp
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sbp2,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  4 usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

I am still a n00b when it comes to this stuff so any and all help is greatly appreciated.
And just to answer the obvious, yes the sound knob is turn up and yes I have searched the forums for an answer, but none seem to apply.

Thanks once again,
-SD-

---

### Post by LostSouLz on 2007-11-15
u could try this 

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Strangerdave on 2007-11-15
Yeah thanks,  I have the restricted formats installed (or at least they should be), but I still hear them.

-SD-

---

### Post by Strangerdave on 2007-11-25
*bump*

Would anyone know about this issue?  I have reinstalled Gutsy and still have the same issues, I hear the start up sound but no other music.  

-SD-

---

### Post by jcsteele on 2007-11-25
Have you tried using rythmnbox (or any other program) to play your music?

Also, if you goto System->Preferences->Sound and then click on "test" by the "sound playback" option, do you hear anything?

//jcs

---

### Post by Strangerdave on 2007-11-25
Yeah, I have tried exaile, and rhythmbox, but the mp3 won't play.  I have the Ubuntu restricted extras loaded.  I noticed that when I click on the master sound, I can change device, but that doesn't seem to help either.

I am just wondering if I have drivers installed for the sound card, but I am not sure where to look to check that out.

Also when I go into preferences, sound and test, it just hangs there and nothing happens.  I can't even close the dialog box.

-SD-

---

### Post by Yellow Pasque on 2007-11-25
Before you go reinstalling Ubuntu or even switching OS's, see if you can get OSSv4 to work since ALSA is giving you a hard time. See my sig for details.

---

### Post by Speckay on 2008-01-14
I'm having the same issues on my A70. It's nothing to do with the restricted formats though, since wav files won't even play. I noticed though that while using the Live CD, sound works fine and you can listen to wav files ok. The minute though that I log onto the one on my system however, I get the same issues where you hear the log-in sound partially play, and then suddenly stop as if something loading with the desktop messes up the sound somehow. I'm not sure how to fix this, but I've tried using other than ALSA and that doesn't fix it.

I've read about plenty of people with this problem, but no solutions... :S Maybe there's some fresh ideas out there? I'm hoping I don't have to dual boot with Windows forever...

---

