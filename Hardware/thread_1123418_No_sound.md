---
title: "No sound"
date: 2009-04-12
forum: Hardware
---

### Post by fatalist.johannes on 2009-04-12
Everything was fine before I removed my TV card from the mainboard. After I removed my TV card, my onboard sound device stopped working. I also have windows on another hard disk and the sound device just works fine. Don't tell me that the sound may be muted because when I try to open the volume control, an error message appears: "No volume control GStreamer plugins and/or devices found"
also when I type sudo sh /etc/init.d/alsa-utils stop on the terminal, it says:
No soundcards found...'...                                         [fail]
(I opened the same thread before but it became a real mess. I tried to delete it, but i couldn't find how to. If one of the admins can delete that thread, I would be happy)

Here's my lspci and lsmod outputs:

lsmod:

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18944  1 
fat                    57376  1 vfat
ipv6                  263972  8 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44560  0 
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
ppdev                  15748  0 
powernow_k8            22148  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container              11520  0 
video                  25232  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
wmi                    14504  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
parport_pc             39332  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
evdev                  17696  6 
serio_raw              13444  0 
psmouse                45200  0 
k8temp                 12416  0 
gspca_sonixj           23936  0 
gspca_main             29312  1 gspca_sonixj
ftdi_sio               55944  0 
videodev               41344  1 gspca_main
usbserial              39528  1 ftdi_sio
v4l1_compat            22404  1 videodev
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
isp1760                26120  0 
i2c_ali1535            14340  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
i2c_ali1563            14980  0 
i2c_ali15x3            14852  0 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
amd64_agp              18184  1 
soundcore              15328  1 snd
uli526x                23440  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ali_agp                13696  0 
agpgart                42184  3 drm,amd64_agp,ali_agp
i2c_core               31892  3 i2c_ali1535,i2c_ali1563,i2c_ali15x3
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
ext3                  133256  2 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  8 
crc_t10dif              9984  1 sd_mod
pata_ali               16516  0 
pata_acpi              12160  0 
sg                     39732  0 
usb_storage            82624  1 
libusual               30356  1 usb_storage
sata_uli               12292  4 
ata_generic            12932  0 
ohci_hcd               32016  0 
ehci_hcd               43788  0 
libata                178208  4 pata_ali,pata_acpi,sata_uli,ata_generic
usbcore               149488  10 gspca_sonixj,gspca_main,ftdi_sio,usbserial,isp1760,usb_storage,libusual,ohci_hcd,ehci_hcd
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5

lspci:

00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:05.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)

---

### Post by fatalist.johannes on 2009-04-12
My sound card rarely works. Sometimes when I start ubuntu, the sound comes back, but after a restart, the sound goes away. I don't want to reinstall ubuntu because I don't want to lose the programs, updates etc. that I installed. Does anybody know what my problem is?

---

### Post by fatalist.johannes on 2009-04-16
I guess I have to remove and reinstall my sound card. How can I do that?

---

