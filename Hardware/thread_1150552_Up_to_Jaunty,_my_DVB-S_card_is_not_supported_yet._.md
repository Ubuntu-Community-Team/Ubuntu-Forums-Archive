---
title: "Up to Jaunty, my DVB-S card is not supported yet. Any hope?"
date: 2009-05-06
forum: Hardware
---

### Post by tarekeldeeb on 2009-05-06
Hello all,

I have upgrade to jaunty, works perfect and smooth.
My problem is still there .. no HW support for my twinhan DVB-S 1027 card.

here's my kernel log section, the device is not dead .. somthing is still missing .. the kernel module does not support my device, not listed.

```

May  6 13:09:20 home-pc kernel: [    9.436134] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
May  6 13:09:20 home-pc kernel: [    9.436188] cx8800 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
May  6 13:09:20 home-pc kernel: [    9.436959] cx88[0]: Your board isn't known (yet) to the driver.  You can
May  6 13:09:20 home-pc kernel: [    9.436961] cx88[0]: try to pick one of the existing card configs via
May  6 13:09:20 home-pc kernel: [    9.436961] cx88[0]: card=<n> insmod option.  Updating to the latest
May  6 13:09:20 home-pc kernel: [    9.436962] cx88[0]: version might help as well.
May  6 13:09:20 home-pc kernel: [    9.436966] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
May  6 13:09:20 home-pc kernel: [    9.436968] cx88[0]:    card=0 -> UNKNOWN/GENERIC
May  6 13:09:20 home-pc kernel: [    9.436969] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
May  6 13:09:20 home-pc kernel: [    9.436971] cx88[0]:    card=2 -> GDI Black Gold
May  6 13:09:20 home-pc kernel: [    9.436972] cx88[0]:    card=3 -> PixelView
May  6 13:09:20 home-pc kernel: [    9.436974] cx88[0]:    card=4 -> ATI TV Wonder Pro
May  6 13:09:20 home-pc kernel: [    9.436975] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
May  6 13:09:20 home-pc kernel: [    9.436977] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
May  6 13:09:20 home-pc kernel: [    9.436979] cx88[0]:    card=7 -> MSI TV-@nywhere Master
May  6 13:09:20 home-pc kernel: [    9.436980] cx88[0]:    card=8 -> Leadtek Winfast DV2000
May  6 13:09:20 home-pc kernel: [    9.436982] cx88[0]:    card=9 -> Leadtek PVR 2000
May  6 13:09:20 home-pc kernel: [    9.436984] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
May  6 13:09:20 home-pc kernel: [    9.436985] cx88[0]:    card=11 -> Prolink PlayTV PVR
May  6 13:09:20 home-pc kernel: [    9.436987] cx88[0]:    card=12 -> ASUS PVR-416
May  6 13:09:20 home-pc kernel: [    9.436988] cx88[0]:    card=13 -> MSI TV-@nywhere
May  6 13:09:20 home-pc kernel: [    9.436990] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
May  6 13:09:20 home-pc kernel: [    9.436991] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
May  6 13:09:20 home-pc kernel: [    9.436993] cx88[0]:    card=16 -> KWorld LTV883RF
May  6 13:09:20 home-pc kernel: [    9.436995] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
May  6 13:09:20 home-pc kernel: [    9.436996] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
May  6 13:09:20 home-pc kernel: [    9.436998] cx88[0]:    card=19 -> Conexant DVB-T reference design
May  6 13:09:20 home-pc kernel: [    9.437000] cx88[0]:    card=20 -> Provideo PV259
May  6 13:09:20 home-pc kernel: [    9.437001] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
May  6 13:09:20 home-pc kernel: [    9.437003] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
May  6 13:09:20 home-pc kernel: [    9.437004] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
May  6 13:09:20 home-pc kernel: [    9.437006] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
May  6 13:09:20 home-pc kernel: [    9.437008] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
May  6 13:09:20 home-pc kernel: [    9.437010] cx88[0]:    card=26 -> IODATA GV/BCTV7E
May  6 13:09:20 home-pc kernel: [    9.437011] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
May  6 13:09:20 home-pc kernel: [    9.437013] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
May  6 13:09:20 home-pc kernel: [    9.437015] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
May  6 13:09:20 home-pc kernel: [    9.437016] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
May  6 13:09:20 home-pc kernel: [    9.437018] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
May  6 13:09:20 home-pc kernel: [    9.437020] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
May  6 13:09:20 home-pc kernel: [    9.437021] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
May  6 13:09:20 home-pc kernel: [    9.437023] cx88[0]:    card=34 -> ATI HDTV Wonder
May  6 13:09:20 home-pc kernel: [    9.437025] cx88[0]:    card=35 -> WinFast DTV1000-T
May  6 13:09:20 home-pc kernel: [    9.437026] cx88[0]:    card=36 -> AVerTV 303 (M126)
May  6 13:09:20 home-pc kernel: [    9.437028] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
May  6 13:09:20 home-pc kernel: [    9.437030] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
May  6 13:09:20 home-pc kernel: [    9.437031] cx88[0]:    card=39 -> KWorld DVB-S 100
May  6 13:09:20 home-pc kernel: [    9.437033] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
May  6 13:09:20 home-pc kernel: [    9.437035] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
May  6 13:09:20 home-pc kernel: [    9.437037] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
May  6 13:09:20 home-pc kernel: [    9.437038] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
May  6 13:09:20 home-pc kernel: [    9.437040] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
May  6 13:09:20 home-pc kernel: [    9.437042] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
May  6 13:09:20 home-pc kernel: [    9.437044] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
May  6 13:09:20 home-pc kernel: [    9.437045] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
May  6 13:09:20 home-pc kernel: [    9.437047] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
May  6 13:09:20 home-pc kernel: [    9.437048] cx88[0]:    card=49 -> PixelView PlayTV P7000
May  6 13:09:20 home-pc kernel: [    9.437050] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
May  6 13:09:20 home-pc kernel: [    9.437052] cx88[0]:    card=51 -> WinFast DTV2000 H ver. I (old)
May  6 13:09:20 home-pc kernel: [    9.437053] cx88[0]:    card=52 -> Geniatech DVB-S
May  6 13:09:20 home-pc kernel: [    9.437055] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
May  6 13:09:20 home-pc kernel: [    9.437057] cx88[0]:    card=54 -> Norwood Micro TV Tuner
May  6 13:09:20 home-pc kernel: [    9.437058] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
May  6 13:09:20 home-pc kernel: [    9.437060] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
May  6 13:09:20 home-pc kernel: [    9.437062] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
May  6 13:09:20 home-pc kernel: [    9.437064] cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
May  6 13:09:20 home-pc kernel: [    9.437066] cx88[0]:    card=59 -> DViCO FusionHDTV 5 PCI nano
May  6 13:09:20 home-pc kernel: [    9.437067] cx88[0]:    card=60 -> Pinnacle Hybrid PCTV
May  6 13:09:20 home-pc kernel: [    9.437069] cx88[0]:    card=61 -> Winfast TV2000 XP Global
May  6 13:09:20 home-pc kernel: [    9.437070] cx88[0]:    card=62 -> PowerColor RA330
May  6 13:09:20 home-pc kernel: [    9.437072] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
May  6 13:09:20 home-pc kernel: [    9.437074] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
May  6 13:09:20 home-pc kernel: [    9.437096] cx88[0]:    card=65 -> DViCO FusionHDTV 7 Gold
May  6 13:09:20 home-pc kernel: [    9.437097] cx88[0]:    card=66 -> Prolink Pixelview MPEG 8000GT
May  6 13:09:20 home-pc kernel: [    9.437099] cx88[0]:    card=67 -> Kworld PlusTV HD PCI 120 (ATSC 120)
May  6 13:09:20 home-pc kernel: [    9.437101] cx88[0]:    card=68 -> Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid
May  6 13:09:20 home-pc kernel: [    9.437103] cx88[0]:    card=69 -> Hauppauge WinTV-HVR4000(Lite) DVB-S/S2
May  6 13:09:20 home-pc kernel: [    9.437104] cx88[0]:    card=70 -> TeVii S460 DVB-S/S2
May  6 13:09:20 home-pc kernel: [    9.437106] cx88[0]:    card=71 -> Omicom SS4 DVB-S/S2 PCI
May  6 13:09:20 home-pc kernel: [    9.437108] cx88[0]:    card=72 -> TBS 8920 DVB-S/S2
May  6 13:09:20 home-pc kernel: [    9.437109] cx88[0]:    card=73 -> TeVii S420 DVB-S
May  6 13:09:20 home-pc kernel: [    9.437111] cx88[0]:    card=74 -> Prolink Pixelview Global Extreme
May  6 13:09:20 home-pc kernel: [    9.437112] cx88[0]:    card=75 -> PROF 7300 DVB-S/S2
May  6 13:09:20 home-pc kernel: [    9.437114] cx88[0]:    card=76 -> WinFast DTV2000 H ver. J (new)
May  6 13:09:20 home-pc kernel: [    9.437116] cx88[0]: subsystem: 1822:0023, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
May  6 13:09:20 home-pc kernel: [    9.437119] cx88[0]: TV tuner type -1, Radio tuner type -1

```

How can I add my card to the list?

Thanks in advance,
Tarek

---

### Post by megacrypto on 2009-09-03
same issue here.. any luck?

---

### Post by tarekeldeeb on 2009-09-04
No
:confused:

---

### Post by megacrypto on 2009-09-04
this is as far as i got until now:
1. get the vanilla kernel 2.6.27.10 from kernel.org
2. get the patch for the Twinhan (attached)
3. I installed Ubuntu 8.10 Desktop
4. did the following as soon as the installation completed:

```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r) subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libtheora-dev libxvidcore4-dev  libvorbis-dev faad usbmount

sudo apt-get install mercurial kernel-package libncurses5-dev 

cd /usr/src
sudo chmod -x /etc/kernel/postinst.d/nvidia-common
sudo apt-get remove nvidia-common
sudo tar xvf /home/user/linux-2.6.27.10.tar.bz2 -C /usr/src
sudo ln -s linux-2.6.27.10 linux
cd linux
sudo cp /boot/config-`uname -r` ./.config 
sudo cp /boot/config-`uname -r` .config 
sudo patch -p1 < /home/user/kernel-2.6.27.10-twinhan.patch
sudo make oldconfig 
sudo make-kpkg clean
sudo fakeroot make-kpkg --initrd --append-to-version=-dvb kernel_image kernel_headers 
cd ..
sudo dpkg -i linux-image-2.6.27.10-dvb_2.6.27.10-dvb-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.27.10-dvb_2.6.27.10-dvb-10.00.Custom_i386.deb
sudo reboot 


```

I had to remove the nvidia-common because it causes some error when I installed the kernel deb's.

now this is what i got after i restarted:

```

mylin@homeserver:~$ dmesg | grep -i dvb
[    0.000000] Linux version 2.6.27.10-dvb (root@homeserver) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Fri Sep 4 22:49:36 EET 2009
[   14.464681] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   14.464744] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   14.464930] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   14.464992] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   14.465116] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   14.465242] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   14.465635] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   14.465699] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   14.466134] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   14.466197] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   14.466260] cx88[0]:    card=39 -> KWorld DVB-S 100
[   14.466321] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   14.466385] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   14.466464] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   14.466527] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   14.466592] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   14.466719] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   14.467091] cx88[0]:    card=52 -> Geniatech DVB-S
[   14.467152] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   14.467372] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   14.467823] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   14.467886] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   14.468138] cx88[0]:    card=68 -> Twinhan VP-1027 DVB-S
mylin@homeserver:~$ lsmod|grep cx8
cx8802                 23812  0
cx8800                 38208  0
cx88xx                 75432  2 cx8802,cx8800
ir_common              48388  1 cx88xx
i2c_algo_bit           14340  1 cx88xx
videodev               41600  3 tuner,cx8800,cx88xx
compat_ioctl32          9600  1 cx8800
tveeprom               20356  1 cx88xx
v4l2_common            20096  2 tuner,cx8800
i2c_core               31892  5 tuner,cx88xx,i2c_algo_bit,tveeprom,v4l2_common
videobuf_dma_sg        20740  3 cx8802,cx8800,cx88xx
videobuf_core          26628  4 cx8802,cx8800,cx88xx,videobuf_dma_sg
btcx_risc              12808  3 cx8802,cx8800,cx88xx


```

as you can see the last line in the dmesg has a new card "Twinhan VP-1027", but for some reason (yet I have to figure out) it is not directly recognized by ubuntu ?!

And if I try to:
```
sudo modprobe cx88-dvb

```

I get the following error:
```

FATAL: Error inserting cx88_dvb (/lib/modules/2.6.27.10-dvb/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

```

?!?!

---

### Post by tarekeldeeb on 2009-09-04
> **megacrypto said:**
> this is as far as i got until now:
1. get the vanilla kernel 2.6.27.10 from kernel.org
2. get the patch for the Twinhan (attached)
3. I installed Ubuntu 8.10 Desktop
4. did the following as soon as the installation completed:

```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r) subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libtheora-dev libxvidcore4-dev  libvorbis-dev faad usbmount

sudo apt-get install mercurial kernel-package libncurses5-dev 

cd /usr/src
sudo chmod -x /etc/kernel/postinst.d/nvidia-common
sudo apt-get remove nvidia-common
sudo tar xvf /home/user/linux-2.6.27.10.tar.bz2 -C /usr/src
sudo ln -s linux-2.6.27.10 linux
cd linux
sudo cp /boot/config-`uname -r` ./.config 
sudo cp /boot/config-`uname -r` .config 
sudo patch -p1 < /home/user/kernel-2.6.27.10-twinhan.patch
sudo make oldconfig 
sudo make-kpkg clean
sudo fakeroot make-kpkg --initrd --append-to-version=-dvb kernel_image kernel_headers 
cd ..
sudo dpkg -i linux-image-2.6.27.10-dvb_2.6.27.10-dvb-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.27.10-dvb_2.6.27.10-dvb-10.00.Custom_i386.deb
sudo reboot 


```

I had to remove the nvidia-common because it causes some error when I installed the kernel deb's.

now this is what i got after i restarted:

```

mylin@homeserver:~$ dmesg | grep -i dvb
[    0.000000] Linux version 2.6.27.10-dvb (root@homeserver) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Fri Sep 4 22:49:36 EET 2009
[   14.464681] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   14.464744] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   14.464930] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   14.464992] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   14.465116] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   14.465242] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   14.465635] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   14.465699] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   14.466134] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   14.466197] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   14.466260] cx88[0]:    card=39 -> KWorld DVB-S 100
[   14.466321] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   14.466385] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   14.466464] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   14.466527] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   14.466592] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   14.466719] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   14.467091] cx88[0]:    card=52 -> Geniatech DVB-S
[   14.467152] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   14.467372] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   14.467823] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   14.467886] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   14.468138] cx88[0]:    card=68 -> Twinhan VP-1027 DVB-S
mylin@homeserver:~$ lsmod|grep cx8
cx8802                 23812  0
cx8800                 38208  0
cx88xx                 75432  2 cx8802,cx8800
ir_common              48388  1 cx88xx
i2c_algo_bit           14340  1 cx88xx
videodev               41600  3 tuner,cx8800,cx88xx
compat_ioctl32          9600  1 cx8800
tveeprom               20356  1 cx88xx
v4l2_common            20096  2 tuner,cx8800
i2c_core               31892  5 tuner,cx88xx,i2c_algo_bit,tveeprom,v4l2_common
videobuf_dma_sg        20740  3 cx8802,cx8800,cx88xx
videobuf_core          26628  4 cx8802,cx8800,cx88xx,videobuf_dma_sg
btcx_risc              12808  3 cx8802,cx8800,cx88xx


```

as you can see the last line in the dmesg has a new card "Twinhan VP-1027", but for some reason (yet I have to figure out) it is not directly recognized by ubuntu ?!

And if I try to:
```
sudo modprobe cx88-dvb

```

I get the following error:
```

FATAL: Error inserting cx88_dvb (/lib/modules/2.6.27.10-dvb/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

```

?!?!

I tried this flow before with no success either !

I think we are a single step away from the solution
:)

---

### Post by megacrypto on 2009-09-04
try this after everything i mentioned before:
```

sudo -s
cd /etc/modprobe.d
echo "options cx88xx card=68" > cx88xx
modprobe -r cx8800
modprobe cx8800
reboot

```
Note: the card no. in card=xxxx is the number i got from the list above

i got the card working and i can watch tv on kaffeine using this link:
[http://ubuntuforums.org/showthread.php?t=246959&highlight=dvb-s+1025](http://ubuntuforums.org/showthread.php?t=246959&highlight=dvb-s+1025)
i used it to setup kaffeine

now im trying to get the remote to work

---

### Post by tarekeldeeb on 2009-09-04
> **megacrypto said:**
> try this after everything i mentioned before:
```

sudo -s
cd /etc/modprobe.d
echo "options cx88xx card=68" > cx88xx
modprobe -r cx8800
modprobe cx8800
reboot

```
Note: the card no. in card=xxxx is the number i got from the list above

i got the card working and i can watch tv on kaffeine using this link:
[http://ubuntuforums.org/showthread.php?t=246959&highlight=dvb-s+1025](http://ubuntuforums.org/showthread.php?t=246959&highlight=dvb-s+1025)
i used it to setup kaffeine

now im trying to get the remote to work

ok I shall try it. Thank you for your help.

If you came to something about the remote, please post it here.

---

