---
title: "mplayer stucks on t61 with hardy 8.04"
date: 2008-05-13
forum: Hardware
---

### Post by nkchenz on 2008-05-13
I have installed the latest restricted nvdia drivers, mplayer can't play .avi files, it just stucks at the first few frames

At first, the color is not right both in totem and realplayer, obviously some color is missing, but after i disable the option tools.perf.hardware.XVideo, color in realplayer is ok, but totem is still wrong


ideer@ideer:/home/chenz$ uname -a
Linux ideer 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
ideer@ideer:/home/chenz$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
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
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
ideer@ideer:/home/chenz$ lsmod
Module                  Size  Used by
af_packet              23812  2 
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
uinput                 10240  1 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
container               5632  0 
bay                     6912  0 
dock                   11280  1 bay
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
reiserfs              239616  1 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
pcmcia                 40876  0 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
thinkpad_acpi          51836  0 
nvram                   9992  2 thinkpad_acpi
psmouse                40336  0 
serio_raw               7940  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
ricoh_mmc               4352  0 
sdhci                  19076  0 
yenta_socket           27276  1 
mmc_core               51460  1 sdhci
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  13056  9 
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_hda_intel         344728  6 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
ac                      6916  0 
battery                14212  0 
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
nvidia               7825536  26 
iwl4965               105844  0 
iwlwifi_mac80211      219108  1 iwl4965
cfg80211               15112  1 iwlwifi_mac80211
i2c_core               24832  1 nvidia
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
wmi_acer                9644  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
soundcore               8800  1 snd
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
pata_acpi               8320  0 
sg                     36880  0 
sd_mod                 30720  8 
usbhid                 31872  0 
hid                    38784  1 usbhid
ahci                   28420  7 
ata_piix               19588  0 
libata                159344  4 ata_generic,pata_acpi,ahci,ata_piix
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
e1000                 125760  0 
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  9 
ideer@ideer:/home/chenz$

---

