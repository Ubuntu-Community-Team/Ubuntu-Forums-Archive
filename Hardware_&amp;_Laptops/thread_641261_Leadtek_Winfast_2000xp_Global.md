---
title: "Leadtek Winfast 2000/xp Global"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by Milos_SD on 2007-12-15
I have this tv card it have conexant chip. How can I get it to work?

Here is lspci output:

```

05:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)

```

lspci -v
```

05:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: LeadTek Research Inc. Unknown device 6618
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

05:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
        Subsystem: LeadTek Research Inc. Unknown device 6618
        Flags: medium devsel, IRQ 17
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

```

lspci -n
```

05:01.0 0400: 14f1:8800 (rev 05)
05:01.1 0480: 14f1:8801 (rev 05)

```


And here is dmesg output:

```

[  38.294938] cx2388x v4l2 driver version 0.0.6 loaded

[   38.295011] cx88[0]: Your board isn't known (yet) to the driver.  You can

[   38.295012] cx88[0]: try to pick one of the existing card configs via

[   38.295013] cx88[0]: card=<n> insmod option.  Updating to the latest

[   38.295013] cx88[0]: version might help as well.

[   38.295015] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:

[   38.295017] cx88[0]:    card=0 -> UNKNOWN/GENERIC

[   38.295018] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models

[   38.295020] cx88[0]:    card=2 -> GDI Black Gold

[   38.295021] cx88[0]:    card=3 -> PixelView

[   38.295022] cx88[0]:    card=4 -> ATI TV Wonder Pro

[   38.295024] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert

[   38.295025] cx88[0]:    card=6 -> AverTV Studio 303 (M126)

[   38.295026] cx88[0]:    card=7 -> MSI TV-@nywhere Master

[   38.295028] cx88[0]:    card=8 -> Leadtek Winfast DV2000

[   38.295029] cx88[0]:    card=9 -> Leadtek PVR 2000

[   38.295030] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI

[   38.295032] cx88[0]:    card=11 -> Prolink PlayTV PVR

[   38.295033] cx88[0]:    card=12 -> ASUS PVR-416

[   38.295034] cx88[0]:    card=13 -> MSI TV-@nywhere

[   38.295036] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T

[   38.295037] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1

[   38.295038] cx88[0]:    card=16 -> KWorld LTV883RF

[   38.295040] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q

[   38.295041] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T

[   38.295042] cx88[0]:    card=19 -> Conexant DVB-T reference design

[   38.295044] cx88[0]:    card=20 -> Provideo PV259

[   38.295045] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus

[   38.295046] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV

[   38.295048] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T

[   38.295049] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models

[   38.295050] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)

[   38.295052] cx88[0]:    card=26 -> IODATA GV/BCTV7E

[   38.295053] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)

[   38.295055] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T

[   38.295056] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI

[   38.295058] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T

[   38.295059] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold

[   38.295060] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550

[   38.295062] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD

[   38.295063] cx88[0]:    card=34 -> ATI HDTV Wonder

[   38.295064] cx88[0]:    card=35 -> WinFast DTV1000-T

[   38.295066] cx88[0]:    card=36 -> AVerTV 303 (M126)

[   38.295067] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S

[   38.295068] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S

[   38.295069] cx88[0]:    card=39 -> KWorld DVB-S 100

[   38.295071] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid

[   38.295072] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)

[   38.295074] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro

[   38.295075] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702

[   38.295077] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital

[   38.295078] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert

[   38.295079] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid

[   38.295081] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV

[   38.295082] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe

[   38.295083] cx88[0]:    card=49 -> PixelView PlayTV P7000

[   38.295085] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10

[   38.295086] cx88[0]:    card=51 -> WinFast DTV2000 H

[   38.295087] cx88[0]:    card=52 -> Geniatech DVB-S

[   38.295089] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T

[   38.295090] cx88[0]:    card=54 -> Norwood Micro TV Tuner

[   38.295092] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM

[   38.295093] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder

[   38.295095] CORE cx88[0]: subsystem: 107d:6618, board: UNKNOWN/GENERIC [card=0,autodetected]

[   38.610769] cx88[0]/0: found at 0000:05:01.0, rev: 5, irq: 17, latency: 32, mmio: 0xfa000000

[   38.631827] tuner 0-0061: chip found @ 0xc2 (cx88[0])

[   38.640031] cx2388x alsa driver version 0.0.6 loaded

[   38.648156] cx88[0]/0: registered device video0 [v4l2]

[   38.648168] cx88[0]/0: registered device vbi0

[   38.657442] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards

```

Maybe it will help that it is a new card that have "vista certified logo on the box" :(

---

### Post by mariuz on 2008-01-18
I used this repository for my card (xc3028 tuner) 

You must have the kernel headers and build dependencies (here is how to use the )


sudo apt-get install mercurial linux-headers-$(uname -r) linux-source build-essential

hg clone  [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)

cd v4l-dvb-experimental
make
sudo make install


After that you will need the firmware from this 
cd /lib/firmware
wget [http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz)
tar xvzf firmware_v4.tgz

add the folowing line in 
/etc/modprobe.d/options
options cx88xx card=59

reboot


here is the url where is discribed about the firmware and other linuxtv related
[http://mcentral.de/wiki/index.php/Em2880#Firmware](http://mcentral.de/wiki/index.php/Em2880#Firmware)
[http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial](http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial)

---

