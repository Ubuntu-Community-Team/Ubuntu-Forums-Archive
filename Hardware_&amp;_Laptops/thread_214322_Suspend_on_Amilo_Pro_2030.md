---
title: "Suspend on Amilo Pro 2030"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by acojlo on 2006-07-12
Has anyone succeded with suspend to ram and hibernate on Amilo Pro 2030? Anyway, if not so, can anyone explain me the way on which I should go if I want to enable suspend and hibernate on the hardware?

I remember that hibernate worked with suse 10.0. Now hibernate starts, screen goes off or just blank? speakers produced one noisy tone, but computer stays turned on. Only possible solution then is to press turn off button. Next booting is normal.

Suspend to ram is working good when it is to suspend, but when it's to resume - computer turns on - some parts of the computer - I can hear fans and cd-rom, even wlan led turns on - but power led continues to blink and there is nothing on the screen.

**Here is lspci output:**

> 0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]
 802.11g Wireless LAN Controller (rev 02)
0000:00:0c.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:00:0c.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Ho                                                              st Controller
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controll                                                              er (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82                                                              3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                                              oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                                              oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/                                                              K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8                                                              237 AC97 Audio Controller (rev 60)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Contro                                                              ller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev                                                               78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3                                                              344 (rev 01)

**Here is lsmod output:**

> Module                  Size  Used by
ppp_deflate             6432  0
zlib_deflate           24248  1 ppp_deflate
bsd_comp                6272  0
ppp_async              13280  1
crc_ccitt               2240  1 ppp_async
ppp_generic            33556  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7456  1 ppp_generic
ipv6                  286976  22
via                    48256  1
drm                    88792  2 via
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
parport_pc             37988  0
ppdev                   9668  0
parport                39400  2 parport_pc,ppdev
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nls_cp437               5888  1
vfat                   14496  1
fat                    55548  1 vfat
nls_utf8                2240  2
ntfs                  111728  1
dm_mod                 63256  0
af_packet              24520  4
p4_clockmod             6244  0
speedstep_lib           4580  1 p4_clockmod
freq_table              4928  2 cpufreq_stats,p4_clockmod
sr_mod                 17988  0
sbp2                   25060  0
snd_seq_midi            9600  0
snd_seq_midi_event      7520  1 snd_seq_midi
snd_seq                58160  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 41948  0
bcm43xx               141868  0
snd_via82xx_modem      16392  6
snd_via82xx            31096  1
gameport               16776  1 snd_via82xx
via_rhine              25988  0
ieee80211softmac       31584  1 bcm43xx
snd_mpu401_uart         8640  1 snd_via82xx
snd_ac97_codec        100224  2 snd_via82xx_modem,snd_via82xx
snd_ac97_bus            2400  1 snd_ac97_codec
yenta_socket           30124  1
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               7748  0
mii                     6176  1 via_rhine
psmouse                40004  0
snd_rawmidi            26848  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9228  3 snd_seq_midi,snd_seq,snd_rawmidi
ieee80211              38952  2 bcm43xx,ieee80211softmac
ieee80211_crypt         6528  1 ieee80211
snd_pcm                96708  5 snd_via82xx_modem,snd_via82xx,snd_ac97_codec
snd_timer              26884  2 snd_seq,snd_pcm
snd_page_alloc         11304  3 snd_via82xx_modem,snd_via82xx,snd_pcm
pcspkr                  2244  0
snd                    60004  21 snd_seq,snd_via82xx_modem,snd_via82xx,snd_mpu401_uart,snd_ac97_codec,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore              10784  1 snd
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
i2c_viapro              9108  0
i2c_core               22848  2 i2c_acpi_ec,i2c_viapro
via_agp                10304  1
agpgart                36784  2 drm,via_agp
sg                     40160  0
evdev                  10176  2
ext3                  148104  1
jbd                    65876  1 ext3
ide_generic             1504  0
ehci_hcd               36104  0
uhci_hcd               35408  0
usbcore               139076  3 ehci_hcd,uhci_hcd
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ide_cd                 35780  0
cdrom                  41440  2 sr_mod,ide_cd
via82cxxx               9796  0 [permanent]
sd_mod                 20448  5
generic                 5124  0
sata_via               10340  4
libata                 83440  1 sata_via
scsi_mod              145960  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                13768  0
processor              26344  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

---

### Post by acojlo on 2006-07-12
Ok, Does Dapper 6.06 686 kernel include support for SATA hard drives?

---

### Post by jenner on 2006-07-15
Hi. I have a 2060 and it works fine to me. The only problem that I have is with the modem. Have you resolve this problem?

---

### Post by acojlo on 2006-07-19
> **jenner said:**
> Hi. I have a 2060 and it works fine to me. The only problem that I have is with the modem. Have you resolve this problem?

Just install slmodemd

---

