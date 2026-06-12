---
title: "Toshiba Qosmio F10-120 boot errors"
date: 2010-10-11
forum: Hardware
---

### Post by kmarien on 2010-10-11
I installed UNR on my Toshiba Qosmio F10-120 laptop. When I boot UNR, I get some warnings about firmware not loaded and some others which are in the attached kern.log

Can you help me solve these problems because I think it is about hardware that is not properly installed, maybe not supported.

After this warnings, without pause, UNR starts up and functions normally. I think that the hardware errors are about a tv tuner card/chip and a modem. I cannot test this because I don't use them.

Kris

---

### Post by kmarien on 2010-10-12
Here are the lines of the kern.log that I don't understand and those problems need to be fixed is needed:


```
Oct 12 20:35:48 Toshiba kernel: [   22.460957] ivtv0: Initializing card 0
Oct 12 20:35:48 Toshiba kernel: [   22.460967] ivtv0: Unknown card: vendor/device: [4444:0016]
Oct 12 20:35:48 Toshiba kernel: [   22.461247] ivtv0:               subsystem vendor/device: [1179:0001]
Oct 12 20:35:48 Toshiba kernel: [   22.461544] ivtv0:               cx23416 based
Oct 12 20:35:48 Toshiba kernel: [   22.461773] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
Oct 12 20:35:48 Toshiba kernel: [   22.462046] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
Oct 12 20:35:48 Toshiba kernel: [   22.462450] ivtv0: card you have to the ivtv-devel mailinglist ([www.ivtvdriver.org]("http://www.ivtvdriver.org/"))
Oct 12 20:35:48 Toshiba kernel: [   22.462813] ivtv0: Prefix your subject line with [UNKNOWN IVTV CARD].
Oct 12 20:35:48 Toshiba kernel: [   22.472093] ivtv 0000:02:09.0: enabling device (0000 -> 0002)
Oct 12 20:35:48 Toshiba kernel: [   22.472104] ivtv 0000:02:09.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 12 20:35:48 Toshiba kernel: [   22.490190] tveeprom 0-0050: Huh, no eeprom present (err=-6)?
Oct 12 20:35:48 Toshiba kernel: [   22.490196] tveeprom 0-0050: Encountered bad packet header [04]. Corrupt or not a Hauppauge eeprom.
Oct 12 20:35:48 Toshiba kernel: [   22.490200] ivtv0: Invalid EEPROM


Oct 12 20:35:48 Toshiba kernel: [   22.702611] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
Oct 12 20:35:48 Toshiba kernel: [   22.706081] wm8775 0-001b: I2C: cannot write 000 to register R23
Oct 12 20:35:48 Toshiba kernel: [   22.724618] wm8775 0-001b: I2C: cannot write 000 to register R7
Oct 12 20:35:48 Toshiba kernel: [   22.731348] type=1505 audit(1286908548.974:10):  operation="profile_load" pid=775 name="/usr/bin/evince-thumbnailer"
Oct 12 20:35:48 Toshiba kernel: [   22.744377] wm8775 0-001b: I2C: cannot write 021 to register R11
Oct 12 20:35:48 Toshiba kernel: [   22.745299] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 12 20:35:49 Toshiba kernel: [   22.765502] wm8775 0-001b: I2C: cannot write 102 to register R12
Oct 12 20:35:49 Toshiba kernel: [   22.776927] wm8775 0-001b: I2C: cannot write 000 to register R13
Oct 12 20:35:49 Toshiba kernel: [   22.793773] type=1505 audit(1286908549.038:11):  operation="profile_load" pid=793 name="/usr/lib/cups/backend/cups-pdf"
Oct 12 20:35:49 Toshiba kernel: [   22.796552] wm8775 0-001b: I2C: cannot write 1d4 to register R14
Oct 12 20:35:49 Toshiba kernel: [   22.809416] wm8775 0-001b: I2C: cannot write 1d4 to register R15
Oct 12 20:35:49 Toshiba kernel: [   22.826971] wm8775 0-001b: I2C: cannot write 1bf to register R16
Oct 12 20:35:49 Toshiba kernel: [   22.849957] wm8775 0-001b: I2C: cannot write 185 to register R17
Oct 12 20:35:49 Toshiba kernel: [   22.861188] wm8775 0-001b: I2C: cannot write 0a2 to register R18
Oct 12 20:35:49 Toshiba kernel: [   22.871731] wm8775 0-001b: I2C: cannot write 005 to register R19
Oct 12 20:35:49 Toshiba kernel: [   22.884526] wm8775 0-001b: I2C: cannot write 07a to register R20
Oct 12 20:35:49 Toshiba kernel: [   22.893126] wm8775 0-001b: I2C: cannot write 102 to register R21


Oct 12 20:35:50 Toshiba kernel: [   23.787685] cx25840 0-0044: firmware: requesting v4l-cx23885-avcore-01.fw
Oct 12 20:35:50 Toshiba kernel: [   23.797211] cx25840 0-0044: firmware load i2c failure



Oct 12 20:35:50 Toshiba kernel: [   24.006502] wm8775 0-001b: I2C: cannot write 0c0 to register R21
Oct 12 20:35:50 Toshiba kernel: [   24.009691] wm8775 0-001b: I2C: cannot write 1d4 to register R14
Oct 12 20:35:50 Toshiba kernel: [   24.016270] wm8775 0-001b: I2C: cannot write 1d4 to register R15
Oct 12 20:35:50 Toshiba kernel: [   24.019343] wm8775 0-001b: I2C: cannot write 102 to register R21
Oct 12 20:35:50 Toshiba kernel: [   24.090985] tuner 0-0060: tuner type not set
Oct 12 20:35:50 Toshiba kernel: [   24.097811] wm8775 0-001b: I2C: cannot write 0c0 to register R21
Oct 12 20:35:50 Toshiba kernel: [   24.100955] wm8775 0-001b: I2C: cannot write 1d4 to register R14
Oct 12 20:35:50 Toshiba kernel: [   24.107204] wm8775 0-001b: I2C: cannot write 1d4 to register R15
Oct 12 20:35:50 Toshiba kernel: [   24.114296] wm8775 0-001b: I2C: cannot write 102 to register R21
Oct 12 20:35:50 Toshiba kernel: [   24.173397] tuner 0-0060: tuner type not set
Oct 12 20:35:50 Toshiba kernel: [   24.174149] tuner 0-0060: tuner type not set
Oct 12 20:35:50 Toshiba kernel: [   24.177572] wm8775 0-001b: I2C: cannot write 0c0 to register R21
Oct 12 20:35:50 Toshiba kernel: [   24.186520] wm8775 0-001b: I2C: cannot write 1d4 to register R14
Oct 12 20:35:50 Toshiba kernel: [   24.196788] wm8775 0-001b: I2C: cannot write 1d4 to register R15
Oct 12 20:35:50 Toshiba kernel: [   24.199862] wm8775 0-001b: I2C: cannot write 108 to register R21
Oct 12 20:35:50 Toshiba kernel: [   24.359492] tuner 0-0060: tuner type not set
Oct 12 20:35:50 Toshiba kernel: [   24.362719] wm8775 0-001b: I2C: cannot write 0c0 to register R21
Oct 12 20:35:50 Toshiba kernel: [   24.366154] wm8775 0-001b: I2C: cannot write 1d4 to register R14
Oct 12 20:35:50 Toshiba kernel: [   24.369628] wm8775 0-001b: I2C: cannot write 1d4 to register R15
Oct 12 20:35:50 Toshiba kernel: [   24.373061] wm8775 0-001b: I2C: cannot write 102 to register R21
```

Can you explain this to me? This text also appears when booting the system.

---

