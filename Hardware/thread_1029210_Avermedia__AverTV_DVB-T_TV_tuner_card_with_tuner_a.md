---
title: "Avermedia  AverTV DVB-T TV tuner card with tuner absent message"
date: 2009-01-03
forum: Hardware
---

### Post by tungsten on 2009-01-03
I've got an AverTV (AverMedia) DVB-T digital PCI TV card, which after looking through these any many other forums, I still cannot get to work. I'm also using Ubuntu 8.10, Intrepid Ibex.

I've been testing it using 'TVTIME', which spots the S-VIDEO and COMPOSITE inputs, but not the TUNER, which isn't surprising as the logs show the 'tuner absent' message.

dmesg gives me :-

> [   15.162221] bttv: driver version 0.9.17 loaded
[   15.162227] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   15.162359] bttv: Bt8xx card found (0).
[   15.162394] bttv 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.162414] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 17, latency: 32, mmio: 0xfddff000
[   15.162440] bttv0: detected: AverMedia AverTV DVB-T 761 [card=124], PCI subsystem ID is 1461:0761
[   15.162450] bttv0: using: AverMedia AverTV DVB-T 761 [card=124,autodetected]
[   15.162506] bttv0: gpio: en=00000000, out=00000000 in=0094000d [init]
[   15.162603] bttv0: tuner absent
[   15.162820] bttv0: registered device video0
[   15.162935] bttv0: registered device vbi0
[   15.162965] bttv0: PLL: 28636363 => 35468950 .. ok
[   15.192592] bttv0: add subdevice "dvb0"
[   15.192804] input: bttv IR (card=124) as /devices/pci0000:00/0000:00:1e.0/0000:02:02.0/input/input5
[   15.238104] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input6
[   15.483349] bt878: AUDIO driver version 0.0.0 loaded
[   15.483393] bt878: Bt878 AUDIO function found (0).
[   15.483415] bt878 0000:02:02.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.483424] bt878_probe: card id=[0x7611461],[ AverMedia AverTV DVB-T 761 ] has DVB functions.
[   15.483437] bt878(0): Bt878 (rev 17) at 02:02.1, irq: 17, latency: 32, memory: 0xfddfe000
[   15.505352] DVB: registering new adapter (bttv0)



and lsmod :-

> Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
ipv6                  263972  18 
binfmt_misc            16904  1 
af_packet              25728  2 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
container              11520  0 
ac                     12292  0 
mt352                  14468  0 
lp                     17156  0 
sp887x                 15236  1 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
dvb_bt8xx              22916  0 
dvb_core               86272  1 dvb_bt8xx
bt878                  17464  1 dvb_bt8xx
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
evdev                  17696  6 
bttv                  171028  2 dvb_bt8xx,bt878
serio_raw              13444  0 
videodev               41344  1 bttv
v4l1_compat            22404  1 videodev
ir_common              48900  1 bttv
compat_ioctl32          9344  1 bttv
psmouse                45200  0 
i2c_algo_bit           14340  1 bttv
v4l2_common            19840  1 bttv
videobuf_dma_sg        20612  1 bttv
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
videobuf_core          26628  2 bttv,videobuf_dma_sg
btcx_risc              12552  1 bttv
tveeprom               20228  1 bttv
snd_seq_oss            38528  0 
nvidia               6909268  36 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
i2c_core               31892  8 mt352,sp887x,dvb_bt8xx,bttv,i2c_algo_bit,v4l2_common,tveeprom,nvidia
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
button                 14224  0 
pcspkr                 10624  0 
snd                    63268  19 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
iptable_nat            13448  0 
nf_nat                 25368  1 iptable_nat
nf_conntrack_ipv4      21900  3 iptable_nat,nf_nat
nf_conntrack           72032  3 iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  0 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22916  2 iptable_nat,ip_tables
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usb_storage            82752  1 
libusual               30356  1 usb_storage
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                178208  3 ata_piix,pata_acpi,ata_generic
r8169                  36100  0 
mii                    13440  1 r8169
scsi_mod              155212  5 usb_storage,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


from dmesg you can see that my card type is 124. My tuner type.... well that's a different matter. Under the sticker on the tuner, the tuner is made by 'Microtune', and is a PAL type (which is good, seeing as I'm in the UK !), but doesn't appear to be either of the Microtune tuners shown in some of the tuner lists I've seen.

Anyone any ideas?? Thanks.

---

### Post by tungsten on 2009-01-25
I guess know-one has any idea then!

---

### Post by roberto.eiberle on 2009-01-27
you should try kaffeine, tvtime looks for an analogue tuner which your card simply does not have. I am using that same card and it works fine out of the box but only with kaffeine or vlc (more complicated)

---

