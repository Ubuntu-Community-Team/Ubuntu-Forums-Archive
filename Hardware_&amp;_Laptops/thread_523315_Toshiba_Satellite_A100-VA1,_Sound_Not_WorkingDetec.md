---
title: "Toshiba Satellite A100-VA1, Sound Not Working/Detected"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by brian10161 on 2007-08-11
Hello, I just installed Ubuntu 7.04 Feisty onto my Toshiba Satellite A100-VA1. It originally came with Windows Vista Home Basic, and I decided to install Linux on it. Seeing as everyone raves about Ubuntu, I thought I'd give it a shot. Everything worked, except for Sound. I would really like to determine why it's not working, considering sound is quite necessary when it comes to using a computer to it's fullest potential.

Anyway, heres the lspci result I got:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

I have installed all the updates. At first before the updates, there was no sound card detected in the mixer, it looked as though only my Modem was showing up there, after updating, I now have 2 cards that show up.

I'm a complete nub when it comes to Linux, I need help to even install a simple program lol

Any help would be greatly appreciated :)

Please let me know if you need any additional information :)

sudo lsmod result:

Module                  Size  Used by
nls_utf8                3072  1 
ntfs                  107764  1 
usb_storage            72256  1 
libusual               17936  1 usb_storage
wlan_wep                7936  1 
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
cpufreq_conservative     8200  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
button                  8720  0 
ac                      6020  0 
sbs                    15652  0 
video                  16388  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
battery                10756  0 
container               5248  0 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
joydev                 10816  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wlan_scan_sta          14976  1 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_rate_sample        14080  1 
pcmcia                 39212  0 
ath_pci                97312  0 
wlan                  204868  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
serio_raw               7940  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
ath_hal               192592  3 ath_rate_sample,ath_pci
pcspkr                  4224  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                38920  0 
i2c_piix4               9740  0 
i2c_core               22656  2 i2c_ec,i2c_piix4
ati_agp                10124  0 
agpgart                35400  1 ati_agp
af_packet              23816  10 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  5 
8139too                27648  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
generic                 5124  0 [permanent]
atiixp                  7440  0 [permanent]
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
sata_sil               12808  2 
ata_generic             9092  0 
libata                125720  2 sata_sil,ata_generic
scsi_mod              142348  5 usb_storage,sbp2,sg,sd_mod,libata
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  5 usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by mattedm on 2007-08-13
Hello Brian, 

I have the same model as you and had exactly the same symptoms you described.  I could not get sound even after setting all the volumes up.   This thread describes the fix I used today, I only had to go through the first steps up until the reboot and the sound was there.

[http://ubuntuforums.org/showthread.php?t=473425](http://ubuntuforums.org/showthread.php?t=473425)

Hope this works for you!

Matt

---

