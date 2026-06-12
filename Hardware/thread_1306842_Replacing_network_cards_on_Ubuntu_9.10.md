---
title: "Replacing network cards on Ubuntu 9.10"
date: 2009-10-30
forum: Hardware
---

### Post by robertoneto123 on 2009-10-30
Hello,

My on-board network card had a hardware problem, so I'm replacing it. But it seams that Ubuntu recognizes it, but cannot use it to do anything.

I'm following the post [http://ubuntuforums.org/showpost.php?p=1102399&postcount=29](http://ubuntuforums.org/showpost.php?p=1102399&postcount=29) , and I'm not sure of why some stuff are different:

When I do the lspci command, I get:

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

So I understand that the network card is recognized, correct?

The lsmod command returns:
Module                  Size  Used by
ufs                    75524  0 
qnx4                    8576  0 
hfsplus                73568  0 
hfs                    43232  0 
minix                  27588  0 
ntfs                   98240  0 
vfat                   10716  0 
msdos                   7836  0 
fat                    51452  2 vfat,msdos
jfs                   177380  0 
xfs                   512064  0 
exportfs                4412  1 xfs
reiserfs              229288  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
rndis_host              7356  1 rndis_wlan
cdc_ether               4924  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
binfmt_misc             8356  1 
lp                      8964  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
dm_crypt               12928  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   6688  0 
soundcore               7264  1 snd
parport_pc             31940  1 
psmouse                56180  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
parport                35340  3 lp,ppdev,parport_pc
serio_raw               5280  0 
squashfs               22912  1 
aufs                  149420  1 
nls_cp437               5372  1 
isofs                  31620  1 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
floppy                 54916  0 
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  3 usbnet,8139too,8139cp
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

Is there any driver missing?

The "dmesg | grep eth" gives me:

[    3.432459] eth0: RealTek RTL8139 at 0xa000, 00:e0:4c:4d:16:48, IRQ 20
[   93.207494] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  103.729009] eth0: no IPv6 routers present
[  268.844419] eth0: link down

Anybody has a clue of what is wrong?

Thanks!

---

