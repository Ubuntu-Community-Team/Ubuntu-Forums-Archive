---
title: "Toshiba PCI TV Tuner type W"
date: 2011-01-28
forum: Hardware
---

### Post by kmarien on 2011-01-28
On my Toshiba Qosmio F10-120 laptop with Windows XP Media Centre Edition I installed Ubuntu 10.04 LTS Desktop Edition.

I have some error messages during boot and those are recorded in dmesg.log.

My guess is they are related to my tv tuner. I already installed the firmware from ivtv.

Here is the output for dmseg | grep ivtv:

```
kmarien@kmarien-toshiba:~$ dmesg | grep ivtv
[   23.807427] ivtv: Start initialization, version 1.4.1
[   24.208236] ivtv0: Initializing card 0
[   24.208245] ivtv0: Unknown card: vendor/device: [4444:0016]
[   24.208518] ivtv0:               subsystem vendor/device: [1179:0001]
[   24.208815] ivtv0:               cx23416 based
[   24.209044] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   24.209316] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   24.209720] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[   24.210083] ivtv0: Prefix your subject line with [UNKNOWN IVTV CARD].
[   24.216077] ivtv 0000:02:09.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   24.228741] ivtv0: Invalid EEPROM
[   24.261511] cx25840 0-0044: cx25  0-21 found @ 0x88 (ivtv i2c driver #0)
[   24.304261] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   24.307633] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   24.430822] IRQ 11/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.431358] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   24.432079] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   24.432179] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   24.432277] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   24.432380] ivtv0: Registered device radio0 for encoder radio
[   24.432383] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   24.433172] ivtv: End initialization
[   25.065014] ivtv 0000:02:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   25.076449] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   25.296156] ivtv0: Encoder revision: 0x02060039
kmarien@kmarien-toshiba:~$ 

```I actually can not test my tv tuner because I don't have devices to connect to the laptop for the moment.
Does this output looks allright and should the tuner work?


I also have some i2c errors in the dmesg.log that I think they are related to the tv tuner.
See the output of dmesg | grep wm8775:

```
kmarien@kmarien-toshiba:~$ dmesg | grep wm8775
[   24.307633] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   24.310811] wm8775 0-001b: I2C: cannot write 000 to register R23
[   24.314233] wm8775 0-001b: I2C: cannot write 000 to register R7
[   24.320141] wm8775 0-001b: I2C: cannot write 021 to register R11
[   24.329971] wm8775 0-001b: I2C: cannot write 102 to register R12
[   24.336580] wm8775 0-001b: I2C: cannot write 000 to register R13
[   24.347176] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   24.359695] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   24.366302] wm8775 0-001b: I2C: cannot write 1bf to register R16
[   24.382539] wm8775 0-001b: I2C: cannot write 185 to register R17
[   24.405812] wm8775 0-001b: I2C: cannot write 0a2 to register R18
[   24.417091] wm8775 0-001b: I2C: cannot write 005 to register R19
[   24.422122] wm8775 0-001b: I2C: cannot write 07a to register R20
[   24.430521] wm8775 0-001b: I2C: cannot write 102 to register R21
[   25.493143] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   25.496378] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   25.499450] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   25.502637] wm8775 0-001b: I2C: cannot write 102 to register R21
[   25.551420] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   25.555371] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   25.560391] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   25.566390] wm8775 0-001b: I2C: cannot write 102 to register R21
[   25.636146] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   25.643987] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   25.651090] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   25.659464] wm8775 0-001b: I2C: cannot write 108 to register R21
[   25.785546] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   25.789610] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   25.794891] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   25.802045] wm8775 0-001b: I2C: cannot write 102 to register R21
[   35.159865] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   35.190218] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   35.221921] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   35.272557] wm8775 0-001b: I2C: cannot write 108 to register R21
[   35.770748] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   35.796549] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   35.836380] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   35.882487] wm8775 0-001b: I2C: cannot write 102 to register R21

```Does anybody knows what those i2c write errors mean and how they can be fixed?

---

