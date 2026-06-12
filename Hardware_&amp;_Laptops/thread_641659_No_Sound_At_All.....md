---
title: "No Sound At All...."
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by Pgi947 on 2007-12-15
Hi folks, Now I have no need for XP on my laptop its gone full time ubuntu, So a few days ago I installed 7.10 gutsy, have to say I'm impressed, come a long way over the years :-)

The only MAJOR issue I've hit is that I have no sound what so ever...

Never had any audio issues on previous ubuntu versions I've used, just wondering if anyone can help me out  as I'm not sure what I should be looking for...

My LSMOD info:
[quote=LSMOD]Module                  Size  Used by
ipv6                  273892  8 
wlan_wep                8064  1 
af_packet              24840  4 
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
binfmt_misc            12936  1 
fglrx                 656352  43 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
container               5504  0 
button                  8976  0 
dock                   10656  0 
video                  18060  0 
ac                      6148  0 
sbs                    19592  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         262552  1 
snd_pcm_oss            44800  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35328  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
pcmcia                 41388  0 
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 11328  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
wlan_scan_sta          15104  1 
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lmpcm_usb               7168  0 
ath_rate_sample        14208  1 
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ath_pci                98336  0 
wlan                  206660  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
serio_raw               8068  0 
8139cp                 25088  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
ath_hal               192720  3 ath_rate_sample,ath_pci
snd                    56452  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
pcspkr                  4224  0 
psmouse                39952  0 
ati_agp                10124  0 
i2c_piix4               9740  0 
shpchp                 34580  0 
i2c_core               26112  1 i2c_piix4
agpgart                35016  2 fglrx,ati_agp
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
atiixp                  7056  0 [permanent]
ide_core              116804  2 ide_cd,atiixp
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  5 usbhid,lmpcm_usb,ehci_hcd,ohci_hcd
sata_sil               12168  2 
ata_generic             8452  0 
libata                125168  2 sata_sil,ata_generic
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
paul@paul-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)[/quote]

[IMG]http://i170.photobucket.com/albums/u249/pgi947/alsa1.png[/IMG]

I'm curious why alsa says "00" under 'Master' but i can't seem to be able to change it...

Thanks for any help which may come my way...

---

