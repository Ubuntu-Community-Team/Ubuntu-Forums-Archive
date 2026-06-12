---
title: "Omnibook XE3 + DLINK DWL-650"
date: 2009-11-30
forum: Hardware
---

### Post by i_ll_be on 2009-11-30
Hi all,

I have got an old HP Omnibook XE3 from a friend. I decided to install linux mint 6 XFCE on it (based on 8.10).

Everything is quite slow but usable... except all network devices...

I have a DLink DWL-650 PCMCIA wireless card. The system seems to see the card as I can see a network. The issue is that I can see only this one (uncrypted) whereas in my other machine I see several of them. I have tried to uncrypt my router network, but still nothing in wicd...

Screenshot of Wicd :
[IMG]http://www.hiboox.fr/go/images/informatique/wicd,84a9aa9906f394120fcd7e24a8a53e7a.png.html[/IMG]

The revision of the card is 1A, as said on the net it should be "prism" chipset.

Have tried ndiswrapper : many drivers without success

Here are some terminal outputs :

> christian@christian-laptop ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"FreeWifi"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.467 GHz  Access Point: 92:E9:53:08:DF:D2   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-102 dBm  Noise level=-149 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

> christian@christian-laptop ~ $ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
usb_storage            81728  1 
libusual               27156  1 usb_storage
nls_utf8                9856  1 
nls_cp437              13696  2 
vfat                   18816  2 
fat                    57376  1 vfat
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
apm                    26332  2 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
af_packet              25728  2 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  1 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
hostap_cs              63380  0 
hostap                114820  1 hostap_cs
ieee80211_crypt        13572  1 hostap
orinoco_cs             21516  1 
orinoco                48020  1 orinoco_cs
hermes                 14976  2 orinoco_cs,orinoco
joydev                 18368  0 
pcmcia                 43052  2 hostap_cs,orinoco_cs
snd_maestro3           27524  4 
snd_ac97_codec        111652  1 snd_maestro3
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  4 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  1 snd_pcm
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
evdev                  17696  4 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
psmouse                45200  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13444  0 
i2c_piix4              16144  0 
snd                    63268  16 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  1 
i2c_core               31892  1 i2c_piix4
shpchp                 37908  0 
agpgart                42184  1 intel_agp
pcspkr                 10624  0 
pci_hotplug            35236  1 shpchp
yenta_socket           31756  4 
rsrc_nonstatic         19072  1 yenta_socket
soundcore              15328  1 snd
pcmcia_core            43412  5 hostap_cs,orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  6 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
ata_piix               24580  3 
pata_acpi              12160  0 
uhci_hcd               30736  0 
libata                177312  3 ata_generic,ata_piix,pata_acpi
usbcore               148848  4 usb_storage,libusual,uhci_hcd
tulip                  58144  0 
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

> christian@christian-laptop ~ $ lspcmcia
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:04.0)
Socket 0 Device 0:	[orinoco_cs]		(bus ID: 0.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:04.1)

Thanks to help me give a dinosaur a second life !

---

