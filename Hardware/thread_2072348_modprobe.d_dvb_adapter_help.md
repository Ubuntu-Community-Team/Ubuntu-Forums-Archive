---
title: "modprobe.d dvb adapter help"
date: 2012-10-17
forum: Hardware
---

### Post by bilboubu on 2012-10-17
I have created a file options.conf as below to attempt to lock tv cards to certain adapter numbers. I have a compro s350 pci dvbs and a pctv 290 usb dvb-t/t2 tuner.

The saa7134 for the compro seems to be working but not the line for the pctv, any ideas? cxd2820r is what is shows uo as in the tv software tvheadend.



```


# DVB-S card
options saa7134_dvb adapter_nr=0
#dvb-t
options cxd2820r adapter_nr=2

```

lsmod

```
Module                  Size  Used by
rfcomm                 38139  0
bluetooth             158438  3 rfcomm
autofs4                27924  1
dm_crypt               22528  0
nfsd                  229850  2
nfs                   307376  0
lockd                  78804  2 nfsd,nfs
fscache                50642  1 nfs
auth_rpcgss            39597  2 nfsd,nfs
nfs_acl                12771  2 nfsd,nfs
sunrpc                206008  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
snd_hda_codec_hdmi     31775  4
zl10039                12976  1
mt312                  17440  1
snd_hda_intel          32765  1
snd_hda_codec         109562  2 snd_hda_codec_hdmi,snd_hda_intel
tda18271               41188  2
saa7134_dvb            33449  1
snd_hwdep              13276  1 snd_hda_codec
saa7134_alsa           18172  0
videobuf_dvb           13867  1 saa7134_dvb
nvidia              10962290  68
snd_pcm                80845  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,s                                                                                                 aa7134_alsa
snd_seq_midi           13132  0
cxd2820r               28233  2
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
em28xx_dvb             18171  1
dvb_core               94814  3 videobuf_dvb,cxd2820r,em28xx_dvb
rc_pinnacle_pctv_hd    12481  0
joydev                 17393  0
xpad                   17827  0
psmouse                86486  0
ir_lirc_codec          12739  3
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_mce_kbd_decoder     12681  0
ir_sony_decoder        12462  0
snd                    62064  11 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,                                                                                                 snd_hwdep,saa7134_alsa,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_jvc_decoder         12459  0
ir_rc6_decoder         12459  0
ff_memless             12945  1 xpad
rc_rc6_mce             12454  0
ir_rc5_decoder         12459  0
saa7134               153846  2 saa7134_dvb,saa7134_alsa
em28xx                 94221  1 em28xx_dvb
dm_multipath           22710  0
videobuf_dma_sg        18786  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_vmalloc       13336  1 em28xx
ppdev                  12849  0
ir_nec_decoder         12459  0
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0
mceusb                 17791  0
videobuf_core          25409  5 videobuf_dvb,saa7134,em28xx,videobuf_dma_sg,vide                                                                                                 obuf_vmalloc
v4l2_common            15793  2 saa7134,em28xx
videodev               86588  3 saa7134,em28xx,v4l2_common
rc_core                21263  15 rc_pinnacle_pctv_hd,ir_lirc_codec,ir_mce_kbd_de                                                                                                 coder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,sa                                                                                                 a7134,em28xx,ir_nec_decoder,mceusb
tveeprom               17009  2 saa7134,em28xx
serio_raw              13027  0
parport_pc             32114  1
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
coretemp               13269  0
dm_raid45              76451  0
xor                    25987  1 dm_raid45
dm_mirror              21822  0
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1
r8169                  56321  0

```

---

