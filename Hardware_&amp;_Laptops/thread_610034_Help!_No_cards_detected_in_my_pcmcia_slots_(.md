---
title: "Help! No cards detected in my pcmcia slots :("
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by thecellartroll on 2007-11-11
I have just done a clean install of Kubuntu 7.04 on my Toshiba S3000-X4 Laptop

During the install and now, no cards were detected in my pcmcia slots. Currently there's an atheros wlan card and a 3com ethernet card in there.

lspci gives me
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1420
02:04.1 CardBus bridge: Texas Instruments PCI1420
steve@athi-kubuntu:/etc/pcmcia$ modprobe pcmcia
steve@athi-kubuntu:/etc/pcmcia$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 03)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1420
02:04.1 CardBus bridge: Texas Instruments PCI1420

and pccardctl -v ident gives me
Socket 0:
  no product info available
Socket 1:
  no product info available

cardctl status gives me
Socket 0:
  no card
Socket 1:
  no card

Both of the cards work fine under windows, as did the pcmcia slots. I haven't tried the ethernet card, but the wlan card works fine under Kubuntu 7.04 on my other (newer) laptop, and is automatically detected and the correct driver seems to be used.

Any way of getting my pcmcia slots working? Otherwise its windows/office and the charity shop for this old girl...

Thanks in advance!
Steve.

P.S. My lsmod is:
'Module                  Size  Used by
pegasus                27536  0
mii                     6528  1 pegasus
ipv6                  268704  10
nls_cp437               6784  0
isofs                  36284  0
udf                    85252  0
i915                   24448  2
drm                    81044  3 i915
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
cpufreq_stats           7360  0
cpufreq_powersave       2688  0
cpufreq_conservative     8200  0
cpufreq_userspace       5408  0
cpufreq_ondemand        9228  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
tc1100_wmi              8068  0
sony_acpi               6284  0
dev_acpi               12292  0
pcc_acpi               13184  0
dock                   10268  0
ac                      6020  0
sbs                    15652  0
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
button                  8720  0
asus_acpi              17308  0
backlight               7040  1 asus_acpi
video                  16388  0
container               5248  0
battery                10756  0
af_packet              23816  4
lp                     12452  0
fuse                   46612  0
joydev                 10816  0
snd_intel8x0           34204  1
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
pcmcia                 39212  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
yenta_socket           27532  2
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
psmouse                38920  0
serio_raw               7940  0
intel_agp              25116  1
agpgart                35400  3 drm,intel_agp
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
evdev                  11008  4
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
sd_mod                 23428  3
ata_generic             9092  0
floppy                 59524  0
ata_piix               15492  2
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
generic                 5124  0 [permanent]
uhci_hcd               25360  0
usbcore               134280  3 pegasus,uhci_hcd
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

### Post by hbbliss on 2007-11-21
Similar problem. Installed 7.10, most things seem ok. However, it won't now recognize my PCMCIA CDRW hardware. As near as I can tell the PCMCIA card is detected but no software comes up to support the drive. It used to work fine under earlier Ubuntu. Can I install an earlier lib using Synaptic? I have previously used this hardware and it worked fine. The hardware works under Windows. Any help would be appreciated. As an aside it will detect my D-Link ethernet hard and Network Administrator shows that I have a  network connection that needs to be configured. I have not configured it because right now I do not have the cable.

---

