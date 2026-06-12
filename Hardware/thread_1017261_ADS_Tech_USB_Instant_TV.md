---
title: "ADS Tech USB Instant TV"
date: 2008-12-20
forum: Hardware
---

### Post by Rob Maurer on 2008-12-20
Hi, I'm trying to install this device (part # USBAV-704N); not getting too far. From DMESG:

```
[   13.929190] Linux video capture interface: v2.00
[   13.969047] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   13.982985] em28xx v4l2 driver version 0.1.0 loaded
[   13.991849] em28xx new video device (eb1a:2821): interface 0, class 255
[   13.991858] em28xx Has usb audio class
[   13.991860] em28xx #0: Alternate settings: 8
[   13.991862] em28xx #0: Alternate setting 0, max size= 0
[   13.991864] em28xx #0: Alternate setting 1, max size= 1024
[   13.991867] em28xx #0: Alternate setting 2, max size= 1448
[   13.991869] em28xx #0: Alternate setting 3, max size= 2048
[   13.991871] em28xx #0: Alternate setting 4, max size= 2304
[   13.991873] em28xx #0: Alternate setting 5, max size= 2580
[   13.991875] em28xx #0: Alternate setting 6, max size= 2892
[   13.991877] em28xx #0: Alternate setting 7, max size= 3072
[   13.992140] em28xx #0: em28xx chip ID = 18
[   14.263258] em28xx #0: found i2c device @ 0x4a [saa7113h]
[   14.266884] em28xx #0: found i2c device @ 0x60 [remote IR sensor]
[   14.273886] em28xx #0: found i2c device @ 0x86 [tda9887]
[   14.277336] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   14.277343] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   14.277364] HDA Intel 0000:00:10.1: setting latency timer to 64
[   14.286134] em28xx #0: found i2c device @ 0xc6 [tuner (analog)]
[   14.305018] em28xx #0: Your board has no unique USB ID and thus need a hint to be detected.
[   14.305025] em28xx #0: You may try to use card=<n> insmod option to workaround that.
[   14.305028] em28xx #0: Please send an email with this log to:
[   14.305030] em28xx #0: 	V4L Mailing List <video4linux-list@redhat.com>
[   14.305032] em28xx #0: Board eeprom hash is 0x00000000
[   14.305034] em28xx #0: Board i2c devicelist hash is 0x8cad00a0
[   14.305037] em28xx #0: Here is a list of valid choices for the card=<n> insmod option:
[   14.305040] em28xx #0:     card=0 -> Unknown EM2800 video grabber
[   14.305042] em28xx #0:     card=1 -> Unknown EM2750/28xx video grabber
[   14.305045] em28xx #0:     card=2 -> Terratec Cinergy 250 USB
[   14.305047] em28xx #0:     card=3 -> Pinnacle PCTV USB 2
[   14.305049] em28xx #0:     card=4 -> Hauppauge WinTV USB 2
[   14.305051] em28xx #0:     card=5 -> MSI VOX USB 2.0
[   14.305053] em28xx #0:     card=6 -> Terratec Cinergy 200 USB
[   14.305055] em28xx #0:     card=7 -> Leadtek Winfast USB II
[   14.305057] em28xx #0:     card=8 -> Kworld USB2800
[   14.305059] em28xx #0:     card=9 -> Pinnacle Dazzle DVC 90/DVC 100
[   14.305061] em28xx #0:     card=10 -> Hauppauge WinTV HVR 900
[   14.305063] em28xx #0:     card=11 -> Terratec Hybrid XS
[   14.305065] em28xx #0:     card=12 -> Kworld PVR TV 2800 RF
[   14.305067] em28xx #0:     card=13 -> Terratec Prodigy XS
[   14.305070] em28xx #0:     card=14 -> Pixelview Prolink PlayTV USB 2.0
[   14.305072] em28xx #0:     card=15 -> V-Gear PocketTV
[   14.305074] em28xx #0:     card=16 -> Hauppauge WinTV HVR 950
[   14.305076] em28xx #0:     card=17 -> Pinnacle PCTV HD Pro Stick
[   14.305078] em28xx #0:     card=18 -> Hauppauge WinTV HVR 900 (R2)
[   14.305080] em28xx #0:     card=19 -> PointNix Intra-Oral Camera
[   14.305082] em28xx #0:     card=20 -> AMD ATI TV Wonder HD 600
[   14.305085] em28xx #0:     card=21 -> eMPIA Technology, Inc. GrabBeeX+ Video Encoder
[   14.305087] em28xx #0:     card=22 -> Unknown EM2750/EM2751 webcam grabber
[   14.305089] em28xx #0:     card=23 -> Huaqi DLCW-130
[   14.305091] em28xx #0:     card=24 -> D-Link DUB-T210 TV Tuner
[   14.305094] em28xx #0:     card=25 -> Gadmei UTV310
[   14.305096] em28xx #0:     card=26 -> Hercules Smart TV USB 2.0
[   14.305098] em28xx #0:     card=27 -> Pinnacle PCTV USB 2 (Philips FM1216ME)
[   14.305100] em28xx #0:     card=28 -> Leadtek Winfast USB II Deluxe
[   14.305103] em28xx #0:     card=29 -> Pinnacle Dazzle DVC 100
[   14.305105] em28xx #0:     card=30 -> Videology 20K14XUSB USB2.0
[   14.305107] em28xx #0:     card=31 -> Usbgear VD204v9
[   14.305109] em28xx #0:     card=32 -> Supercomp USB 2.0 TV
[   14.305111] em28xx #0:     card=33 -> SIIG AVTuner-PVR/Prolink PlayTV USB 2.0
[   14.305113] em28xx #0:     card=34 -> Terratec Cinergy A Hybrid XS
[   14.305115] em28xx #0:     card=35 -> Typhoon DVD Maker
[   14.305117] em28xx #0:     card=36 -> NetGMBH Cam
[   14.305119] em28xx #0:     card=37 -> Gadmei UTV330
[   14.305121] em28xx #0:     card=38 -> Yakumo MovieMixer
[   14.305123] em28xx #0:     card=39 -> KWorld PVRTV 300U
[   14.305125] em28xx #0:     card=40 -> Plextor ConvertX PX-TV100U
[   14.305127] em28xx #0:     card=41 -> Kworld 350 U DVB-T
[   14.305129] em28xx #0:     card=42 -> Kworld 355 U DVB-T
[   14.305131] em28xx #0:     card=43 -> Terratec Cinergy T XS
[   14.305133] em28xx #0:     card=44 -> Terratec Cinergy T XS (MT2060)
[   14.305136] em28xx #0:     card=45 -> Pinnacle PCTV DVB-T
[   14.305138] em28xx #0:     card=46 -> Compro, VideoMate U3
[   14.305140] em28xx #0:     card=47 -> KWorld DVB-T 305U
[   14.305142] em28xx #0:     card=48 -> KWorld DVB-T 310U
[   14.305144] em28xx #0:     card=49 -> MSI DigiVox A/D
[   14.305146] em28xx #0:     card=50 -> MSI DigiVox A/D II
[   14.305148] em28xx #0:     card=51 -> Terratec Hybrid XS Secam
[   14.305150] em28xx #0:     card=52 -> DNT DA2 Hybrid
[   14.305152] em28xx #0:     card=53 -> Pinnacle Hybrid Pro
[   14.305154] em28xx #0:     card=54 -> Kworld VS-DVB-T 323UR
[   14.305156] em28xx #0:     card=55 -> Terratec Hybrid XS (em2882)
[   14.305158] em28xx #0:     card=56 -> Pinnacle Hybrid Pro (2)
[   14.305160] em28xx #0:     card=57 -> Kworld PlusTV HD Hybrid 330
[   14.305162] em28xx #0:     card=58 -> Compro VideoMate ForYou/Stereo
[   14.311834] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   14.771074] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   14.950213] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[   14.950219] em28xx #0: Found Unknown EM2750/28xx video grabber
[   14.950262] em28xx audio device (eb1a:2821): interface 1, class 1
[   14.968107] usbcore: registered new interface driver em28xx
[   14.968655] usbcore: registered new interface driver snd-usb-audio
[   15.800037] lp: driver loaded but no devices found

```

Maybe I need a correct card=<n> number? Anybody work with this one? When I start Kaffeine, I get "Can't bind info socket!!!"
Thanks, Rob

---

### Post by gborzi on 2008-12-31
Hello Rob,
I have a similar USB hybrid TV device, a Dazzle TV Stick. Both syslog and lsusb report the ID as *eb1a:2881*, like your card. I got it to work with Markus Rechberger experimental driver. I've made a package for Hardy which is available [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204578"), just scroll down to my first post there. Hope it works on Intrepid.

Regards.

---

### Post by Rob Maurer on 2008-12-31
Thank you Giuseppe. I found your package and installed it. Still unfortunately I am not successful using the device. DMESG returns:

```
[   13.025937] Linux video capture interface: v2.00
[   13.193224] em28xx v4l2 driver version 0.1.0 loaded
[   13.199698] em28xx new video device (eb1a:2821): interface 0, class 255
[   13.199705] em28xx Has usb audio class
[   13.199707] em28xx #0: Alternate settings: 8
[   13.199709] em28xx #0: Alternate setting 0, max size= 0
[   13.199711] em28xx #0: Alternate setting 1, max size= 1024
[   13.199713] em28xx #0: Alternate setting 2, max size= 1448
[   13.199715] em28xx #0: Alternate setting 3, max size= 2048
[   13.199717] em28xx #0: Alternate setting 4, max size= 2304
[   13.199720] em28xx #0: Alternate setting 5, max size= 2580
[   13.199722] em28xx #0: Alternate setting 6, max size= 2892
[   13.199724] em28xx #0: Alternate setting 7, max size= 3072
[   13.199923] em28xx #0: em28xx chip ID = 18
[   13.430178] em28xx #0: em28xx_i2c_eeprom: i2c_master_recv failed! err [-19]
[   13.430184] em28xx #0: em28xx_i2c_register: em28xx_i2_eeprom failed! retval [-19]
[   13.430188] em28xx #0: em28xx_init_dev: em28xx_i2c_register - errCode [-19]!
[   13.430207] em28xx audio device (eb1a:2821): interface 1, class 1
[   13.430214] em28xx audio device (eb1a:2821): interface 2, class 1
[   13.430245] usbcore: registered new interface driver em28xx

```

I think it may be progress. I very much appreciate any insight you can share. Thanks so much for replying.
Rob Maurer

---

### Post by gborzi on 2008-12-31
Hello Rob,
my dmesg reports
> [  286.016297] usb 1-5.3: new high speed USB device using ehci_hcd and address 1
1
[  286.057050] usb 1-5.3: configuration #1 chosen from 1 choice
[  286.057395] em28xx: new video device (eb1a:2881): interface 0, class 255
[  286.057399] em28xx: device is attached to a USB 2.0 bus
[  286.057403] em28xx #0: Alternate settings: 8
[  286.057405] em28xx #0: Alternate setting 0, max size= 0
[  286.057407] em28xx #0: Alternate setting 1, max size= 0
[  286.057410] em28xx #0: Alternate setting 2, max size= 1448
[  286.057412] em28xx #0: Alternate setting 3, max size= 2048
[  286.057414] em28xx #0: Alternate setting 4, max size= 2304
[  286.057417] em28xx #0: Alternate setting 5, max size= 2580
[  286.057419] em28xx #0: Alternate setting 6, max size= 2892
[  286.057421] em28xx #0: Alternate setting 7, max size= 3072
[  286.226213] attach_inform: tvp5150 detected.
[  286.250229] tvp5150 5-005c: tvp5150am1 detected.
[  287.681203] successfully attached tuner
[  287.685777] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[  287.699450] em28xx #0: V4L2 device registered as /dev/video1
[  287.699456] em2880-dvb.c: DVB Init
[  287.919298] DVB: registering new adapter (em2880 DVB-T)
[  287.919305] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[  287.920237] input: em2880/em2870 remote control as /devices/virtual/input/input31
[  287.942598] em28xx-input.c: remote control handler attached
[  287.942605] em28xx #0: Found Pinnacle Hybrid Pro
and creates /dev/video1 and /dev/dvb/adapter0 when I plug the USB stick. Please check if the modules where actually compiled, they should be in /lib/modules/<kernel version>/updates/dkms/. On my system the command *ls lib/modules/2.6.24-22-generic/updates/dkms/* returns > drx3973d.ko        em28xx-cx25843.ko  mt2060.ko  s921.ko          zl10353.ko
em28xx-aad.ko      em28xx-dvb.ko      mt352.ko   tuner-xc3028.ko
em28xx-audioep.ko  em28xx.ko          nvidia.ko  tuner-xc5000.ko
em28xx-audio.ko    lgdt3304.ko        qt1010.ko  tvp5150.ko
You should have the same result (besides the nvidia.ko module) if the compilation was successful.

---

### Post by gborzi on 2009-01-01
Sorry, I made a mistake, my card is eb1a:2881, your is eb1a:2821. Looking at the list of supported cards of em28xx in the intrepid kernel (it's in /usr/share/doc/linux-doc-<kernel version>/Documentation/video4linux/CARDLIST.em28xx if you have installed the linux-doc package) the only card that has the same USB ID is card number 14, "Pixelview Prolink PlayTV USB 2.0".
Hope it helps.

---

