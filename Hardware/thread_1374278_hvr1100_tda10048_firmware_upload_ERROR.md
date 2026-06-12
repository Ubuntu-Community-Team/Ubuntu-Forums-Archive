---
title: "hvr1100: tda10048_firmware_upload ERROR"
date: 2010-01-06
forum: Hardware
---

### Post by PelztierZwo on 2010-01-06
Hi,

I'm having trouble installing my WinTV-HVR 1100 DVB Card. I already did the following three things.

1. I downloaded, made and installed v4l. Rebooted.
2. I was confused by the message saying that some tda-file was missing.
2. I googled for a file called dvb-fe-tda10048*.fw, downloaded and moved it to /lib/firmware.

I'm getting strange errors. dmesg prints:

> [   52.760087] DVB: registering new adapter (saa7133[0])
[   52.760089] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   53.641260] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   53.641265] saa7134 0000:05:00.0: firmware: requesting dvb-fe-tda10048-1.0.fw
[   53.690850] tda10048_firmware_upload: firmware read 24878 bytes.
[   53.690852] tda10048_firmware_upload: firmware uploading
[   58.950014] tda10048_firmware_upload: firmware uploaded
[   61.740013] tda18271_write_regs: [0-0060|M] ERROR: idx = 0x13, len = 1, i2c_transfer returned: -5
[   63.390021] tda18271_write_regs: [0-0060|M] ERROR: idx = 0x1, len = 7, i2c_transfer returned: -5
[   63.390063] tda18271_channel_configuration: [0-0060|M] error -5 on line 185
[   63.390103] tda18271_set_analog_params: [0-0060|M] error -5 on line 1046
[   63.551260] tda18271_write_regs: [0-0060|M] ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[   63.551303] tda18271_toggle_output: [0-0060|M] error -5 on line 48
[   64.860011] tda18271_write_regs: [0-0060|M] ERROR: idx = 0xc, len = 4, i2c_transfer returned: -5
[   64.980012] tda18271_write_regs: [0-0060|M] ERROR: idx = 0x1, len = 7, i2c_transfer returned: -5
[   64.980055] tda18271_channel_configuration: [0-0060|M] error -5 on line 185
[   64.980094] tda18271_set_analog_params: [0-0060|M] error -5 on line 1046
[   66.720013] tda18271_write_regs: [0-0060|M] ERROR: idx = 0x1, len = 7, i2c_transfer returned: -5
[   66.720018] tda18271_channel_configuration: [0-0060|M] error -5 on line 185
[   66.720022] tda18271_set_analog_params: [0-0060|M] error -5 on line 1046
[   67.980014] tda18271_write_regs: [0-0060|M] ERROR: idx = 0x1, len = 7, i2c_transfer returned: -5
[   67.980019] tda18271_channel_configuration: [0-0060|M] error -5 on line 185
[   67.980023] tda18271_set_analog_params: [0-0060|M] error -5 on line 1046What could I do to resolve this problem? I'm guessing I've got the wrong firmware or tda*.fw is somehow wrong / corrupted / missing / whatever.

I hope someone is able to help me. Thank you.

06.01.: I'm using Kubuntu 9.10.

-PelztierZwo

---

### Post by demiurg on 2010-10-21
I'm having similar problems with Ubuntu 10.10

> 
[   42.445966] DVB: registering new adapter (saa7133[0])
[   42.445977] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   43.029561] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   43.059428] tda10048_firmware_upload: firmware read 24878 bytes.
[   43.059439] tda10048_firmware_upload: firmware uploading
[   44.588539] tda18271_write_regs: [1-0060|M] ERROR: idx = 0x25, len = 1, i2c_transfer returned: -5
[   44.588612] tda18271_channel_configuration: [1-0060|M] error -5 on line 119
[   44.588675] tda18271_set_analog_params: [1-0060|M] error -5 on line 1045
[   45.741194] ppdev: user-space parallel port driver
[   48.172053] tda10048_firmware_upload: firmware uploaded
[   81.088894] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   82.008045] tda18271_write_regs: [1-0060|M] ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[   82.008059] tda18271_init: [1-0060|M] error -5 on line 830
[   82.008067] tda18271_tune: [1-0060|M] error -5 on line 908
[   82.008074] tda18271_set_analog_params: [1-0060|M] error -5 on line 1045




Any suggestions ?

---

### Post by mmanzato on 2011-01-11
In 10.10 the dvb-fe-tda10048*.fw firmware comes with the linux-firmware-nonfree package (sudo apt-get install linux-firmware-nonfree). I am using MythBuntu with Hauppauge HVR-1120 DVB-T (triangular shaped).

When I load the firmware the card is able to tune to many channels (250+ services near Verona, Italy, with w_scan). However when the firmware is not loaded the card is still able to tune some services. So, I wonder what exactly this firmware is for.

That said, I am also having problems with this card. Although channels/services are found, 99% of the times I am not able to tune to and watch most/any of them on MythTV. I am experiencing the same TDA18271 dmesg errors.

Any hints?

---

