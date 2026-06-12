---
title: "No output from webcam 2.0, unknown brand"
date: 2011-05-13
forum: Hardware
---

### Post by Matt-In-The-Hat on 2011-05-13
I have just bought an unbranded webcam (setting myself up for disappointment I know) that has a mic and uses usb 2.0. The mic works but the cam doesn't output anything. Anyone any ideas? Other threads ask for the outputs of lsusb and lsmod, so here they are:

output of lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 002: ID 090c:937b Feiya Technology Corp. Silicon Motion Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

output of lsmod:
Module                  Size  Used by
tda1004x               15082  1 
saa7134_dvb            23366  0 
videobuf_dvb            5219  1 saa7134_dvb
dvb_core               88505  1 videobuf_dvb
saa7134_alsa           10412  1 
rc_hauppauge_new        1100  0 
ir_kbd_i2c              5667  0 
binfmt_misc             6599  1 
nvidia               9329739  40 
tda827x                 9252  2 
tda8290                12538  1 
snd_hda_codec_realtek   218492  1 
tuner                  20578  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 saa7134_alsa,snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
joydev                  8767  0 
ir_lirc_codec           3092  0 
lirc_dev                9393  1 ir_lirc_codec
snd_rawmidi            17783  1 snd_seq_midi
uvcvideo               55847  0 
saa7134               148613  2 saa7134_dvb,saa7134_alsa
ir_sony_decoder         1889  0 
ir_jvc_decoder          1950  0 
hid_logitech            8971  0 
v4l2_common            17329  2 tuner,saa7134
ff_memless              4393  1 hid_logitech
snd_seq_midi_event      6047  1 snd_seq_midi
ir_rc6_decoder          2334  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
ir_rc5_decoder          1950  0 
parport_pc             26058  1 
snd_timer              19067  2 snd_pcm,snd_seq
usbhid                 36882  1 hid_logitech
ir_nec_decoder          2014  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               43098  4 tuner,uvcvideo,saa7134,v4l2_common
videobuf_dma_sg         9806  3 saa7134_dvb,saa7134_alsa,saa7134
v4l1_compat            13359  2 uvcvideo,videodev
hid                    67742  2 hid_logitech,usbhid
videobuf_core          16907  3 videobuf_dvb,saa7134,videobuf_dma_sg
ir_common               5167  1 saa7134
snd                    49038  16 saa7134_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2633  0 
serio_raw               4022  0 
intel_agp              26566  0 
ir_core                14654  11 rc_hauppauge_new,ir_kbd_i2c,ir_lirc_codec,ir_sony_decoder,saa7134,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ir_common
tveeprom               11178  1 saa7134
lp                      7342  0 
agpgart                32011  2 nvidia,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
parport                31492  3 ppdev,parport_pc,lp
usb_storage            40204  0 
floppy                 54311  0 
sky2                   45127  0 


Any ideas?

Thanks,

Matthew.

---

### Post by Matt-In-The-Hat on 2011-05-13
Please, I don't want to have to use it on my girlfriend's Windows machine!

Matthew

---

