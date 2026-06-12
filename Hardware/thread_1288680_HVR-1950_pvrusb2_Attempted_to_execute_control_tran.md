---
title: "HVR-1950: pvrusb2: Attempted to execute control transfer when device not ok"
date: 2009-10-11
forum: Hardware
---

### Post by deadland on 2009-10-11
Hi ubuntufriends,

I'M LOST. I try to get the Hauppauge HVR-1950 running on an eee 701 with mythtv on Jaunty and an external settopbox? In general the HVR works. I can watch tv, but a lot of times, when I reboot the machine and the HVR is already plugged in, I get the following dmesg out:

```
Oct 11 14:23:26 centerpc kernel: [  398.732050] pvrusb2: Attempted to execute control transfer when device not ok
Oct 11 14:23:26 centerpc kernel: [  398.832051] pvrusb2: Attempted to execute control transfer when device not ok
Oct 11 14:23:26 centerpc kernel: [  398.932039] pvrusb2: Attempted to execute control transfer when device not ok
```

I'm searching a solution since almost 2 month and perhaps it's the lack of english knowledge, that I don't understand what I have to do.


Thats the dmesg output, when I plugin the HVR after booting the system:

```
Oct 11 14:41:35 centerpc kernel: [  674.948046] usb 1-4: new high speed USB device using ehci_hcd and address 5
Oct 11 14:41:35 centerpc kernel: [  675.121878] usb 1-4: configuration #1 chosen from 1 choice
Oct 11 14:41:35 centerpc kernel: [  675.199896] usbcore: registered new interface driver pvrusb2
Oct 11 14:41:35 centerpc kernel: [  675.199910] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
Oct 11 14:41:35 centerpc kernel: [  675.199918] pvrusb2: Debug mask is 31 (0x1f)
Oct 11 14:41:36 centerpc kernel: [  676.200098] usb 1-4: firmware: requesting v4l-pvrusb2-73xxx-01.fw
Oct 11 14:41:36 centerpc kernel: [  676.217472] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
Oct 11 14:41:36 centerpc kernel: [  676.249260] usb 1-4: USB disconnect, address 5
Oct 11 14:41:36 centerpc kernel: [  676.249973] pvrusb2: Device being rendered inoperable
Oct 11 14:41:38 centerpc kernel: [  678.004059] usb 1-4: new high speed USB device using ehci_hcd and address 6
Oct 11 14:41:38 centerpc kernel: [  678.145942] usb 1-4: configuration #1 chosen from 1 choice
Oct 11 14:41:39 centerpc kernel: [  678.318425] lirc_i2c: chip 0x10005 found @ 0x71 (Hauppauge PVR150)
Oct 11 14:41:39 centerpc kernel: [  678.318513] lirc_dev: lirc_register_plugin: sample_rate: 10
Oct 11 14:41:39 centerpc kernel: [  678.332727] cx25840' 1-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
Oct 11 14:41:39 centerpc kernel: [  678.403156] tuner' 1-0042: chip found @ 0x84 (pvrusb2_a)
Oct 11 14:41:39 centerpc kernel: [  678.448250] tveeprom 1-00a2: Hauppauge model 75111, rev C3E9, serial# 6285352
Oct 11 14:41:39 centerpc kernel: [  678.448262] tveeprom 1-00a2: MAC address is 00-0D-FE-5F-E8-28
Oct 11 14:41:39 centerpc kernel: [  678.448271] tveeprom 1-00a2: tuner model is Philips 18271_8295 (idx 149, type 54)
Oct 11 14:41:39 centerpc kernel: [  678.448280] tveeprom 1-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Oct 11 14:41:39 centerpc kernel: [  678.448288] tveeprom 1-00a2: audio processor is CX25843 (idx 37)
Oct 11 14:41:39 centerpc kernel: [  678.448295] tveeprom 1-00a2: decoder processor is CX25843 (idx 30)
Oct 11 14:41:39 centerpc kernel: [  678.448302] tveeprom 1-00a2: has radio, has IR receiver, has IR transmitter
Oct 11 14:41:39 centerpc kernel: [  678.448319] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
Oct 11 14:41:39 centerpc kernel: [  678.448332] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
Oct 11 14:41:39 centerpc kernel: [  678.448342] pvrusb2: Setting up 6 unique standard(s)
Oct 11 14:41:39 centerpc kernel: [  678.448352] pvrusb2: Set up standard idx=0 name=PAL-M
Oct 11 14:41:39 centerpc kernel: [  678.448359] pvrusb2: Set up standard idx=1 name=PAL-N
Oct 11 14:41:39 centerpc kernel: [  678.448367] pvrusb2: Set up standard idx=2 name=PAL-Nc
Oct 11 14:41:39 centerpc kernel: [  678.448374] pvrusb2: Set up standard idx=3 name=NTSC-M
Oct 11 14:41:39 centerpc kernel: [  678.448382] pvrusb2: Set up standard idx=4 name=NTSC-Mj
Oct 11 14:41:39 centerpc kernel: [  678.448389] pvrusb2: Set up standard idx=5 name=NTSC-Mk
Oct 11 14:41:39 centerpc kernel: [  678.448399] pvrusb2: Initial video standard (determined by device type): NTSC-M
Oct 11 14:41:39 centerpc kernel: [  678.448425] pvrusb2: Device initialization completed successfully.
Oct 11 14:41:39 centerpc kernel: [  678.459128] pvrusb2: registered device video0 [mpeg]
Oct 11 14:41:39 centerpc kernel: [  678.459146] DVB: registering new adapter (pvrusb2-dvb)
Oct 11 14:41:39 centerpc kernel: [  678.490052] cx25840' 1-0044: firmware: requesting v4l-cx25840.fw
Oct 11 14:41:41 centerpc kernel: [  680.380723] cx25840' 1-0044: loaded v4l-cx25840.fw firmware (12559 bytes)
Oct 11 14:41:41 centerpc kernel: [  680.564579] tda829x 1-0042: setting tuner address to 60
Oct 11 14:41:41 centerpc kernel: [  680.617029] tda18271 1-0060: creating new instance
Oct 11 14:41:41 centerpc kernel: [  680.656580] TDA18271HD/C1 detected @ 1-0060
Oct 11 14:41:42 centerpc kernel: [  681.829579] tda829x 1-0042: type set to tda8295+18271
Oct 11 14:41:45 centerpc kernel: [  685.146718] cx25840' 1-0044: Video signal:              not present
Oct 11 14:41:45 centerpc kernel: [  685.146730] cx25840' 1-0044: Detected format:           NTSC-M
Oct 11 14:41:45 centerpc kernel: [  685.146736] cx25840' 1-0044: Specified standard:        NTSC-M
Oct 11 14:41:45 centerpc kernel: [  685.146743] cx25840' 1-0044: Specified video input:     Composite 7
Oct 11 14:41:45 centerpc kernel: [  685.146750] cx25840' 1-0044: Specified audioclock freq: 48000 Hz
Oct 11 14:41:45 centerpc kernel: [  685.154952] cx25840' 1-0044: Detected audio mode:       mono
Oct 11 14:41:45 centerpc kernel: [  685.154961] cx25840' 1-0044: Detected audio standard:   BTSC
Oct 11 14:41:45 centerpc kernel: [  685.154967] cx25840' 1-0044: Audio muted:               no
Oct 11 14:41:45 centerpc kernel: [  685.154973] cx25840' 1-0044: Audio microcontroller:     running
Oct 11 14:41:45 centerpc kernel: [  685.154981] cx25840' 1-0044: Configured audio standard: automatic detection
Oct 11 14:41:45 centerpc kernel: [  685.154988] cx25840' 1-0044: Configured audio system:   BTSC
Oct 11 14:41:45 centerpc kernel: [  685.154995] cx25840' 1-0044: Specified audio input:     Tuner (In8)
Oct 11 14:41:45 centerpc kernel: [  685.155002] cx25840' 1-0044: Preferred audio mode:      stereo
Oct 11 14:41:45 centerpc kernel: [  685.217429] cx25840' 1-0044: firmware: requesting v4l-cx25840.fw
Oct 11 14:41:47 centerpc kernel: [  686.987385] cx25840' 1-0044: loaded v4l-cx25840.fw firmware (12559 bytes)
Oct 11 14:41:49 centerpc kernel: [  689.291833] usb 1-4: firmware: requesting v4l-cx2341x-enc.fw
Oct 11 14:41:52 centerpc kernel: [  691.890084] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
Oct 11 14:41:52 centerpc kernel: [  691.896214] tda829x 1-0042: type set to tda8295
Oct 11 14:41:52 centerpc kernel: [  691.999634] tda18271 1-0060: attaching existing instance
```

```
[   18.912950] lirc_dev: IR Remote Control driver registered, major 61 
[  678.318425] lirc_i2c: chip 0x10005 found @ 0x71 (Hauppauge PVR150)
[  678.318513] lirc_dev: lirc_register_plugin: sample_rate: 10

```

Thats the extract of my lirc hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1300"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Motorola Cable box"
#TRANSMITTER_MODULES="lirc_dev lirc_cmdir lirc_pvr150"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""
```

Well, I really tried to find a solution, but I couldn't. It would be great, if someone could help me.

Thanks in advanced

---

### Post by deadland on 2009-10-11
I seams to be a problem with lirc_i2c, because if I use lirc_pvr150 I can boot my system without problems, but I have no working lirc configuration, which is essential for my mediacenter.

I would be great if someone could post me its hardware.conf

Thanks in advanced

---

