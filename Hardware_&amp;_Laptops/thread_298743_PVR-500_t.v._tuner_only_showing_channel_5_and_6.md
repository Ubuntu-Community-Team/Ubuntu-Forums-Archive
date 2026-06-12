---
title: "PVR-500 t.v. tuner only showing channel 5 and 6"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by gleem on 2006-11-13
I am trying to setup myth tv. Setting up mythtv doesnt seem to be the problem however, installing my hauppange PVR-500 is.

after following these instructions:

[https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)

I found that only channels 5 and 6 appear all black and white. any other channels appear as snow.

prior to setting up mythtv, I tried watching tv through mplayer.... so I know its setting up the correct drivers / firmware..

help please...

---

### Post by gleem on 2006-11-13
bump....

anyone else having this issue.... 

here is my ivtv log

```

[17181337.640000] ivtv:  ==================== START INIT IVTV ====================
[17181337.640000] ivtv:  version 0.7.0 (tagged release) loading
[17181337.640000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17181337.640000] ivtv:  In case of problems please include the debug info between
[17181337.640000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17181337.640000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17181337.640000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17181337.640000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 217
[17181337.640000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17181337.696000] tveeprom 4-0050: Hauppauge model 23552, rev D492, serial# 8142897
[17181337.696000] tveeprom 4-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[17181337.696000] tveeprom 4-0050: TV standards NTSC(M) (eeprom 0x08)
[17181337.696000] tveeprom 4-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[17181337.696000] tveeprom 4-0050: audio processor is CX25843 (idx 37)
[17181337.696000] tveeprom 4-0050: decoder processor is CX25843 (idx 30)
[17181337.696000] tveeprom 4-0050: has radio, has no IR remote
[17181337.696000] ivtv0: This is the first unit of a PVR500
[17181337.740000] tuner 4-0060: TEA5767 detected.
[17181337.740000] tuner 4-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[17181337.740000] tuner 4-0060: type set to 62 (Philips TEA5767HN FM Radio)
[17181337.740000] tuner 4-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17181337.916000] tda9887 4-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17181337.940000] cx25840 4-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17181340.888000] cx25840 4-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17181340.968000] wm8775 4-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17181341.640000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17181341.856000] ivtv0: Encoder revision: 0x02050032
[17181341.856000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17181341.856000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17181341.860000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17181341.860000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17181341.860000] ivtv0: Create encoder radio stream
[17181341.860000] tuner 4-0061: type set to 57 (Philips FQ1236A MK4)
[17181342.084000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[17181342.084000] ivtv:  ======================  NEXT CARD  ======================
[17181342.084000] ivtv1: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17181342.084000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 18 (level, low) -> IRQ 169
[17181342.084000] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[17181342.140000] tuner 5-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[17181342.296000] tda9887 5-0043: chip found @ 0x86 (ivtv i2c driver #1)
[17181342.312000] cx25840 5-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[17181345.232000] cx25840 5-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17181345.304000] wm8775 5-001b: chip found @ 0x36 (ivtv i2c driver #1)
[17181345.356000] tveeprom 5-0050: Hauppauge model 23552, rev D492, serial# 8142897
[17181345.356000] tveeprom 5-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[17181345.356000] tveeprom 5-0050: TV standards NTSC(M) (eeprom 0x08)
[17181345.356000] tveeprom 5-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[17181345.356000] tveeprom 5-0050: audio processor is CX25843 (idx 37)
[17181345.356000] tveeprom 5-0050: decoder processor is CX25843 (idx 30)
[17181345.356000] tveeprom 5-0050: has radio, has no IR remote
[17181345.356000] ivtv1: This is the second unit of a PVR500
[17181345.356000] ivtv1: Correcting tveeprom data: no radio present on second unit
[17181346.060000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17181346.276000] ivtv1: Encoder revision: 0x02050032
[17181346.276000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17181346.276000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17181346.280000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17181346.280000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17181346.280000] tuner 5-0061: type set to 57 (Philips FQ1236A MK4)
[17181346.496000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[17181346.496000] ivtv:  ====================  END INIT IVTV  ==================


```

---

