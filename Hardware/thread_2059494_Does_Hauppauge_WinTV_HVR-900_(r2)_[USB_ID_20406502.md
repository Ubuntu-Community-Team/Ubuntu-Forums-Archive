---
title: "Does Hauppauge WinTV HVR-900 (r2) [USB ID 2040:6502] work with ubuntu 12.04 LTS?"
date: 2012-09-18
forum: Hardware
---

### Post by Nightfly24 on 2012-09-18
I have this DVB+Analog usb tv tuner Hauppauge WinTV HVR-900 (r2) [USB ID 2040:6502]. This used to work under ubuntu 10.04 LTS. But in 12.04 there seems to be a problem.
  I have linux-firmware-nonfree and ivtv-utils installed.
  I am running Ubuntu 12.04.1 LTS 64 bit with all updates installed and the default unity environment.


When I run


```

  
mplayer tv:// -tv driver=v4l2:device=/dev/video1:input=1:norm=PAL 
```


I get a solid green screen and no picture. Here input 1 is the composite input of the card.


```



MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team mplayer: could not connect to socket mplayer: No such file or directory Failed to open LIRC support. You will not be able to use your remote control.  Playing tv://. TV file format detected. Selected driver: v4l2  name: Video 4 Linux 2 input  author: Martin Olschewski   comment: first try, more to come ;-) Selected device: Hauppauge WinTV HVR 900 (R2)  Tuner cap:  Tuner rxs:  Capabilities:  video capture  VBI capture device  tuner  audio  read/write  streaming  supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = NTSC-443; 5 = PAL; 6 = PAL-BG; 7 = PAL-H; 8 = PAL-I; 9 = PAL-DK; 10 = PAL-M; 11 = PAL-N; 12 = PAL-Nc; 13 = PAL-60; 14 = SECAM; 15 = SECAM-B; 16 = SECAM-G; 17 = SECAM-H; 18 = SECAM-DK; 19 = SECAM-L; 20 = SECAM-Lc;  inputs: 0 = Television; 1 = Composite1; 2 = S-Video;  Current input: 1  Current format: YUYV v4l2: current audio mode is : MONO v4l2: ioctl set format failed: Invalid argument v4l2: ioctl set format failed: Invalid argument v4l2: ioctl set format failed: Invalid argument v4l2: ioctl query control failed: Invalid argument v4l2: ioctl query control failed: Invalid argument v4l2: ioctl query control failed: Invalid argument v4l2: ioctl query control failed: Invalid argument Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory [vdpau] Error when calling vdp_device_create_x11: 1 ========================================================================== Opening video decoder: [raw] RAW Uncompressed Video Movie-Aspect is undefined - no prescaling applied. VO: [xv] 640x480 => 640x480 Packed YUY2  Selected video codec: [rawyuy2] vfm: raw (RAW YUY2) ========================================================================== Audio: no sound Starting playback... v4l2: select timeout V:   0.0   2/  2 ??% ??% ??,?% 0 0  v4l2: select timeout V:   0.0   4/  4 ??% ??% ??,?% 0 0  v4l2: select timeout V:   0.0   6/  6 ??% ??% ??,?% 0 0  v4l2: select timeout v4l2: 0 frames successfully processed, 1 frames dropped.  Exiting... (Quit)


```


Here is the dmesg of the card when plugged in..




```



[12742.228097] usb 1-4: new high-speed USB device number 3 using ehci_hcd [12742.367289] em28xx: New device WinTV HVR-900 @ 480 Mbps (2040:6502, interface 0, class 0) [12742.367296] em28xx: Audio Vendor Class interface 0 found [12742.367585] em28xx #0: chip ID is em2882/em2883 [12742.550086] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 02 65 d0 12 5c 03 82 1e 6a 18 [12742.550104] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00 [12742.550120] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b e0 00 00 [12742.550135] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 01 01 00 00 00 00 [12742.550150] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 [12742.550165] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 [12742.550181] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00 [12742.550196] em28xx #0: i2c eeprom 70: 32 00 37 00 38 00 32 00 33 00 39 00 30 00 31 00 [12742.550211] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00 [12742.550226] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 30 00 30 00 00 00 [12742.550241] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 fa fd d0 28 89 [12742.550257] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 1d b7 [12742.550272] em28xx #0: i2c eeprom c0: 13 f0 74 02 01 00 01 79 63 00 00 00 00 00 00 00 [12742.550287] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 fa fd d0 28 89 [12742.550302] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 1d b7 [12742.550317] em28xx #0: i2c eeprom f0: 13 f0 74 02 01 00 01 79 63 00 00 00 00 00 00 00 [12742.550334] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x2bbf3bdd [12742.550338] em28xx #0: EEPROM info: [12742.550340] em28xx #0:   AC97 audio (5 sample rates) [12742.550343] em28xx #0:   500mA max power [12742.550346] em28xx #0:   Table at 0x24, strings=0x1e82, 0x186a, 0x0000 [12742.552590] em28xx #0: Identified as Hauppauge WinTV HVR 900 (R2) (card=18) [12742.555516] tveeprom 15-0050: Hauppauge model 65018, rev B2C0, serial# 1292061 [12742.555523] tveeprom 15-0050: tuner model is Xceive XC3028 (idx 120, type 71) [12742.555529] tveeprom 15-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4) [12742.555534] tveeprom 15-0050: audio processor is None (idx 0) [12742.555537] tveeprom 15-0050: has radio [12742.570297] tuner 15-0061: Tuner -1 found with type(s) Radio TV. [12742.570327] xc2028 15-0061: creating new instance [12742.570332] xc2028 15-0061: type set to XCeive xc2028/xc3028 tuner [12742.573685] xc2028 15-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7 [12742.624056] xc2028 15-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000. [12744.126591] xc2028 15-0061: Loading firmware for type=MTS (4), id 000000000000b700. [12744.153586] xc2028 15-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700. [12744.280963] Registered IR keymap rc-hauppauge [12744.281151] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/rc/rc1/input10 [12744.281541] rc1: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/rc/rc1 [12744.282454] em28xx #0: Config register raw data: 0xd0 [12744.284709] em28xx #0: AC97 vendor ID = 0xffffffff [12744.285829] em28xx #0: AC97 features = 0x6a90 [12744.285832] em28xx #0: Empia 202 AC97 audio processor detected [12744.359211] em28xx #0: v4l2 driver version 0.1.3 [12744.404066] xc2028 15-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000. [12745.915089] MTS (4), id 00000000000000ff: [12745.915100] xc2028 15-0061: Loading firmware for type=MTS (4), id 0000000100000007. [12746.161668] em28xx #0: V4L2 video device registered as video1 [12746.161673] em28xx #0: V4L2 VBI device registered as vbi0 [12746.162845] em28xx-audio.c: probing for em28xx Audio Vendor Class [12746.162848] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger [12746.162851] em28xx-audio.c: Copyright (C) 2007-2011 Mauro Carvalho Chehab [12746.221099] xc2028 15-0061: attaching existing instance [12746.221105] xc2028 15-0061: type set to XCeive xc2028/xc3028 tuner [12746.221109] em28xx #0: em28xx #0/2: xc3028 attached [12746.221113] DVB: registering new adapter (em28xx #0) [12746.221118] DVB: registering adapter 0 frontend 0 (Micronas DRXD DVB-T)... [12746.221869] em28xx #0: Successfully loaded em28xx-dvb [13111.196055] xc2028 15-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000. [13112.720062] MTS (4), id 00000000000000ff: [13112.720072] xc2028 15-0061: Loading firmware for type=MTS (4), id 0000000100000007. [13214.956057] xc2028 15-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000. [13216.479806] MTS (4), id 00000000000000ff: [13216.479816] xc2028 15-0061: Loading firmware for type=MTS (4), id 0000000100000007. [13276.408056] xc2028 15-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000. [13277.932093] MTS (4), id 00000000000000ff: [13277.932104] xc2028 15-0061: Loading firmware for type=MTS (4), id 0000000100000007. [13305.032076] xc2028 15-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000. [13306.556449] MTS (4), id 00000000000000ff: [13306.556460] xc2028 15-0061: Loading firmware for type=MTS (4), id 0000000100000007. [13392.236055] xc2028 15-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000. [13393.760123] MTS (4), id 00000000000000ff: [13393.760133] xc2028 15-0061: Loading firmware for type=MTS (4), id 0000000100000007. [13637.534053] usb 1-4: USB disconnect, device number 3 [13637.534183] em28xx #0: disconnecting em28xx #0 video [13637.560214] em28xx #0: V4L2 device vbi0 deregistered [13637.560335] em28xx #0: V4L2 device video1 deregistered [13637.561237] xc2028 15-0061: destroying instance [13639.772120] usb 1-4: new high-speed USB device number 4 using ehci_hcd [13639.911351] em28xx: New device WinTV HVR-900 @ 480 Mbps (2040:6502, interface 0, class 0) [13639.911357] em28xx: Audio Vendor Class interface 0 found [13639.911637] em28xx #0: chip ID is em2882/em2883 [13640.094262] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 02 65 d0 12 5c 03 82 1e 6a 18 [13640.094280] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00 [13640.094295] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b e0 00 00 [13640.094311] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 01 01 00 00 00 00 [13640.094326] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 [13640.094341] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 [13640.094356] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00 [13640.094371] em28xx #0: i2c eeprom 70: 32 00 37 00 38 00 32 00 33 00 39 00 30 00 31 00 [13640.094386] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00 [13640.094401] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 30 00 30 00 00 00 [13640.094416] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 fa fd d0 28 89 [13640.094432] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 1d b7 [13640.094447] em28xx #0: i2c eeprom c0: 13 f0 74 02 01 00 01 79 63 00 00 00 00 00 00 00 [13640.094462] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 fa fd d0 28 89 [13640.094477] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 1d b7 [13640.094492] em28xx #0: i2c eeprom f0: 13 f0 74 02 01 00 01 79 63 00 00 00 00 00 00 00 [13640.094509] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x2bbf3bdd [13640.094512] em28xx #0: EEPROM info: [13640.094515] em28xx #0:   AC97 audio (5 sample rates) [13640.094517] em28xx #0:   500mA max power [13640.094521] em28xx #0:   Table at 0x24, strings=0x1e82, 0x186a, 0x0000 [13640.097391] em28xx #0: Identified as Hauppauge WinTV HVR 900 (R2) (card=18) [13640.099617] tveeprom 15-0050: Hauppauge model 65018, rev B2C0, serial# 1292061 [13640.099623] tveeprom 15-0050: tuner model is Xceive XC3028 (idx 120, type 71) [13640.099629] tveeprom 15-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4) [13640.099634] tveeprom 15-0050: audio processor is None (idx 0) [13640.099637] tveeprom 15-0050: has radio [13640.112849] tuner 15-0061: Tuner -1 found with type(s) Radio TV. [13640.112877] xc2028 15-0061: creating new instance [13640.112882] xc2028 15-0061: type set to XCeive xc2028/xc3028 tuner [13640.115930] xc2028 15-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7 [13640.164057] xc2028 15-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000. [13641.666643] xc2028 15-0061: Loading firmware for type=MTS (4), id 000000000000b700. [13641.693262] xc2028 15-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700. [13641.820765] Registered IR keymap rc-hauppauge [13641.820958] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/rc/rc2/input11 [13641.821335] rc2: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/rc/rc2 [13641.822256] em28xx #0: Config register raw data: 0xd0 [13641.824526] em28xx #0: AC97 vendor ID = 0xffffffff [13641.825503] em28xx #0: AC97 features = 0x6a90 [13641.825507] em28xx #0: Empia 202 AC97 audio processor detected [13641.899015] em28xx #0: v4l2 driver version 0.1.3 [13641.944064] xc2028 15-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000. [13643.470765] MTS (4), id 00000000000000ff: [13643.470776] xc2028 15-0061: Loading firmware for type=MTS (4), id 0000000100000007. [13643.717713] em28xx #0: V4L2 video device registered as video1 [13643.717718] em28xx #0: V4L2 VBI device registered as vbi0 [13643.718770] em28xx-audio.c: probing for em28xx Audio Vendor Class [13643.718775] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger [13643.718778] em28xx-audio.c: Copyright (C) 2007-2011 Mauro Carvalho Chehab [13643.777148] xc2028 15-0061: attaching existing instance [13643.777154] xc2028 15-0061: type set to XCeive xc2028/xc3028 tuner [13643.777158] em28xx #0: em28xx #0/2: xc3028 attached [13643.777162] DVB: registering new adapter (em28xx #0) [13643.777167] DVB: registering adapter 0 frontend 0 (Micronas DRXD DVB-T)... [13643.777876] em28xx #0: Successfully loaded em28xx-dvb  


```




And here goes the lsmod output


```



lsmod|grep em28xx em28xx_dvb             18579  0  dvb_core              110619  1 em28xx_dvb em28xx_alsa            18305  0  em28xx                109365  2 em28xx_dvb,em28xx_alsa v4l2_common            16454  3 tuner,tvp5150,em28xx videobuf_vmalloc       13589  1 em28xx videobuf_core          26390  2 em28xx,videobuf_vmalloc rc_core                26412  10 rc_hauppauge,ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,em28xx,ir_nec_decoder snd_pcm                97188  3 em28xx_alsa,snd_hda_intel,snd_hda_codec tveeprom               21249  1 em28xx videodev               98259  5 tuner,tvp5150,em28xx,v4l2_common,uvcvideo snd                    78855  14 em28xx_alsa,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device  


```




Isn't this driver mainline now? Or this card is not supported? Or the analog functionality is screwed? 
  I need the analog capture working for this card.
  Please help!

---

### Post by Nightfly24 on 2012-09-18
exactly same issue is being reported by texas instruments blog at 
[http://e2e.ti.com/support/dsp/sitara_arm174_microprocessors/f/416/t/123947.aspx?pi36549=1](http://e2e.ti.com/support/dsp/sitara_arm174_microprocessors/f/416/t/123947.aspx?pi36549=1)

---

