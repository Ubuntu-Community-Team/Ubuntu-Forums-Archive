---
title: "mplayer pvr:// FAIL"
date: 2010-05-24
forum: Hardware
---

### Post by bluerabbit4210 on 2010-05-24
Hi all,

Here on a fresh install of mint9 (based on 10.04), I can't get mplayer to access my ASUS PVR-416 tv capture card

$ mplayer pvr://
```
...
[pvr] Using device /dev/video0
[pvr] Detected ASUS PVR-416
[encoder] device do not support MPEG input.
Failed to open pvr://.

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
```now what stumps me is that dmesg confirms my card is being detected correctly, and `mplayer /dev/video1` (yes that a 1 not a typo) will play video and audio.  what gets me is the line "[encoder] device do not support MPEG input."  what device?  what is mplayer trying to send MPEG input to exactly?  upping the verbosity of mplayer yields nothing.
this card has an mpeg encoder (conexant cx23416-12), so i'm wondering if this is the "device do not support MPEG input"

stumped!

any ideas?  thanks!

---

### Post by dino99 on 2010-05-24
is linux-firmware-nonfree installed ?

---

### Post by bluerabbit4210 on 2010-05-24
it is now.

did a full reboot...nothing new that i can see [EDIT: now `mplayer /dev/video1` has no audio!]
after all this googling this is the first i've heard of this package!

aptitude show says that the package 'currently contains firmware for DVB cards.', but I was under the impression that this card was NOT a DVB card.  I admit I'm still unsure as to the distinction.  

this link: [http://linuxtv.org/wiki/index.php/Hardware_Device_Information](http://linuxtv.org/wiki/index.php/Hardware_Device_Information) seems to say that cx2388x devices aren't DVB's
the tv card has a conexant cx23880 decoder and a cx23416 mpeg encoder.

this link: [http://ivtvdriver.org/index.php/Supported_hardware](http://ivtvdriver.org/index.php/Supported_hardware) states explicitly that my card is not supported by the ivtv driver, but the cx88-blackbird driver should work.

```

$ mplayer /dev/video1
Cannot seek backward in linear streams!
Seek failed
....
Cannot seek backward in linear streams!
Seek failed
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
A: 138.0 V: 138.0 A-V: -0.001 ct: -1.085 4103/4103 11%  1%  0.5% 1 0 
Exiting... (Quit)

``````
$ dmesg | grep cx
[    8.690991] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[    8.691365] cx88[0]: subsystem: 1043:4823, board: ASUS PVR-416 [card=12,autodetected], frontend(s): 0
[    8.691369] cx88[0]: TV tuner type 43, Radio tuner type -1
[    8.691397] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[    8.932459] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[    8.987650] tuner 1-0043: chip found @ 0x86 (cx88[0])
[    9.299797] cx88[0]/2: cx2388x 8802 Driver Manager
[    9.299816] cx88-mpeg driver manager 0000:04:07.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.299825] cx88[0]/2: found at 0000:04:07.2, rev: 5, irq: 22, latency: 32, mmio: 0xfc000000
[    9.299834] IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.299912] cx8800 0000:04:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.299919] cx88[0]/0: found at 0000:04:07.0, rev: 5, irq: 22, latency: 32, mmio: 0xfd000000
[    9.299930] IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.300050] cx88[0]/0: registered device video0 [v4l2]
[    9.300076] cx88[0]/0: registered device vbi0
[    9.300102] cx88[0]/0: registered device radio0
[    9.417429] cx2388x blackbird driver version 0.0.7 loaded
[    9.417433] cx88/2: registering cx8802 driver, type: blackbird access: shared
[    9.417437] cx88[0]/2: subsystem: 1043:4823, board: ASUS PVR-416 [card=12]
[    9.417441] cx88[0]/2: cx23416 based mpeg encoder (blackbird reference design)
[    9.417662] cx88[0]/2-bb: Firmware and/or mailbox pointer not initialized or corrupted
[    9.424054] cx88-mpeg driver manager 0000:04:07.2: firmware: requesting v4l-cx2341x-enc.fw
[   12.043247] cx88[0]/2-bb: Firmware upload successful.
[   12.049772] cx88[0]/2-bb: Firmware version is 0x02060039
[   12.056837] cx88[0]/2: registered device video1 [mpeg]
[   20.870716] cx88[0]/2-bb: VIDIOC_TRY_FMT: w: 720, h: 480, f: 4
``````
$ lspci -nn | grep media
00:08.0 Multimedia audio controller [0401]: ALi Corporation M5455 PCI AC-Link Controller Audio Device [10b9:5455] (rev 20)
04:07.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
04:07.2 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)

``````
$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
nfsd                  238935  13 
exportfs                3437  1 nfsd
nfs                   264702  0 
lockd                  64849  2 nfsd,nfs
nfs_acl                 2245  2 nfsd,nfs
auth_rpcgss            33735  2 nfsd,nfs
dm_crypt               11331  0 
cx88_blackbird         14222  0 
cx2341x                12469  1 cx88_blackbird
tuner_simple           13577  1 
tuner_types            14233  1 tuner_simple
tda9887                 9589  1 
sunrpc                193181  12 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
tda8290                12092  0 
snd_intel8x0           25588  2 
tea5767                 5950  0 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
tuner                  20412  2 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
cx8802                 12841  1 cx88_blackbird
cx8800                 27188  1 cx88_blackbird
snd_rawmidi            19056  1 snd_seq_midi
cx88xx                 72596  3 cx88_blackbird,cx8802,cx8800
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
v4l2_common            15431  5 cx88_blackbird,cx2341x,tuner,cx8800,cx88xx
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ir_common              38875  1 cx88xx
videodev               34361  5 cx88_blackbird,tuner,cx8800,cx88xx,v4l2_common
i2c_algo_bit            5028  1 cx88xx
joydev                  8708  0 
v4l1_compat            13251  1 videodev
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               11102  1 cx88xx
btcx_risc               3624  3 cx8802,cx8800,cx88xx
hid_logitech            7388  0 
soundcore               6620  1 snd
videobuf_dma_sg        10782  4 cx88_blackbird,cx8802,cx8800,cx88xx
i2c_ali15x3             5050  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
shpchp                 28820  0 
k8temp                  3024  0 
ff_memless              4093  1 hid_logitech
videobuf_core          16356  5 cx88_blackbird,cx8802,cx8800,cx88xx,videobuf_dma_sg
i2c_ali1563             5438  0 
uli526x                13126  0 
i2c_ali1535             4725  0 
nvidia               9932176  38 
psmouse                63245  0 
ppdev                   5259  0 
usblp                  10481  0 
parport_pc             25962  1 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
usbhid                 36110  1 hid_logitech
hid                    67032  2 hid_logitech,usbhid
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
ohci1394               26950  0 
usb_storage            39425  0 
softcursor              1189  1 bitblit
amd64_agp               7025  1 
ieee1394               81181  1 ohci1394
ali_agp                 3717  0 
pata_ali                7900  5 
agpgart                31724  3 nvidia,amd64_agp,ali_agp
vga16fb                11385  1 
vgastate                8961  1 vga16fb

``````
$ uname -a
Linux freekbox 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

---

### Post by dino99 on 2010-05-24
googling around: 

some users recompile kernel

into synaptic, searching for "tv": 
maybe try tvtime and/or gnome-dvb-daemon

---

### Post by bluerabbit4210 on 2010-05-24
> **dino99 said:**
> googling around: 
some users recompile kernel
ugh, i was hoping to avoid that

> **dino99 said:**
> 
into synaptic, searching for "tv": 
maybe try tvtime and/or gnome-dvb-daemon
i don't think tvtime will process sound.

i think i'm gonna sleep on it and see if it fixes itself by morning!

---

