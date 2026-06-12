---
title: "cant get Media 150-d TV card with conextant cx23882 chipset working"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by bumbu on 2007-04-01
--------------------update------------2 april 2007---------------------------------------------------

i have found that:
there is no option card at least i think there isnt as i try:

user@xp2600ubuntu:~$ modinfo cx8800
filename:       /lib/modules/2.6.15-28-386/kernel/drivers/media/video/cx88/cx8800.ko
description:    v4l2 driver module for cx2388x based TV cards
author:         Gerd Knorr <kraxel@bytesex.org> [SuSE Labs]
license:        GPL
vermagic:       2.6.15-28-386 preempt 486 gcc-4.0
depends:        video-buf,cx88xx,videodev,btcx-risc,v4l2-common,v4l1-compat
alias:          pci:v000014F1d00008800sv*sd*bc*sc*i*
srcversion:     56100463E86EFE8E78FBB59
parm:           vbi_debug:enable debug messages [vbi] (int)
parm:           vbibufs:number of vbi buffers, range 2-32 (int)
parm:           vid_limit:capture memory limit in megabytes (int)
parm:           irq_debug:enable debug messages [IRQ handler] (int)
parm:           video_debug:enable debug messages [video] (int)
parm:           radio_nr:radio device numbers (array of int)
parm:           vbi_nr:vbi device numbers (array of int)
parm:           video_nr:video device numbers (array of int)

so there is no option card here....

has annyone had the same problem? Or has annyone got a idea? please let me know afther hours of google i came up with nothing...

thanx!!!



--------------------Endof update------------------------------------------------------------------------

Dear Ubuntu forum members

I am trying to get my TV-card installed, it is a Avermedia M150-D card. It uses the conextant cx23882-19 chip and te Conextant mpegII AV-Encoder CX23416-12 chip. It has got composite connectors and a SVHS conector.

i did use this article to get the card working:
[http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D](http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D)
but it didnt work. So i did try google and came up with this:
[http://tvtime.sourceforge.net/problems.html#undetected](http://tvtime.sourceforge.net/problems.html#undetected)
which pretty much describe's my problem (i think):
........"If your card appears as UNKNOWN/GENERIC, then the tuner driver will not be loaded and the card will likely not work. You will need to load the driver with the correct card number."........

So as i don' t use the bttv
chip but the conextant chip's i tried to take a look which module's there i have got to unload (rmmod) and reload again with the card=12 option ([http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D](http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D) uses card number 12 so i assume i have to use this number but here the troubles start. I don' t know which module i have to unload and load again. There are a lot of them  


lsmod |grep cx
cx8800                 32268  0
cx88_dvb             10244  0
cx8802                 11780  1 cx88_dvb
cx88xx                 62368  3 cx8800,cx88_dvb,cx8802
v4l1_compat        14468  1 cx8800
i2c_algo_bit          9608  2 ivtv,cx88xx
v4l2_common       6016  1 cx8800
ir_common            9988  1 cx88xx
btcx_risc               5128  3 cx8800,cx8802,cx88xx
tveeprom               15248  1 cx88xx
mt352                   6788  1 cx88_dvb
or51132                10244  1 cx88_dvb
video_buf_dvb     6660  1 cx88_dvb
videodev               9856  3 cx8800,ivtv,cx88xx
video_buf              22148  5 cx8800,cx88_dvb,cx8802,cx88xx,video_buf_dvb
nxt200x                13444  1 cx88_dvb
lgdt330x               8092  1 cx88_dvb
cx22702                6404  1 cx88_dvb
dvb_pll                11012  4 cx88_dvb,or51132,nxt200x,cx22702
i2c_core               21904  16 i2c_acpi_ec,ivtv,asb100,eeprom,tuner,cx88_dvb,cx88xx,i2c_algo_bit,tveeprom,mt352,or51132,nxt200x,lgdt330x,cx22702,nvidia,i2c_nforce2


So then i tried:

user@xp2600ubuntu:~$ sudo rmmod cx8800
user@xp2600ubuntu:~$ sudo modprobe cx8800 card=12
FATAL: Error inserting cx8800 (/lib/modules/2.6.15-28-386/kernel/drivers/media/video/cx88/cx8800.ko): Unknown symbol in module, or unknown parameter (see dmesg)

so that didnt work, i got the mesg info however:

dmesg | grep card
[17324669.792000] cx88_blackbird: Unknown parameter `card'
[17326010.816000] cx8800: Unknown parameter `card'
[17326213.916000] cx8800: Unknown parameter `card'

So now i am stuck and don't know where to go from here and i hope someone on this forum can help me out. There is some more information which might be useful. I live in the Netherlands and here we have got PAL (PAL-BG i think) and not NTSC as described in the dmesg from the  
[http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D](http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D) site:
"tuner 0-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F)"
, there is another difference the writer of the article has got a tv-card without composite and s-vhs connector and my card has got these connectors. 
I also tried to start tvtime as ROOT but that didnt work either. I hope someone here can help me out! i did put some info here whitch i thought might be useful! Thank you in advance!



$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
0000:01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0000:01:08.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
0000:01:08.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
0000:01:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
0000:03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)




:~$ tvtime -v
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/user/.tvtime/tvtime.xml
cpuinfo: CPU AMD Athlon(tm) XP 2600+, family 6, model 8, stepping 1.
cpuinfo: CPU measured at 2079.690MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 70000000
xfullscreen: Single-head detected, pixel aspect will be calculated.
xfullscreen: Pixel aspect ratio on the primary head is: 1368/1355 == 1.01.
xfullscreen: Using the XFree86-VidModeExtension to calculate fullscreen size.
xfullscreen: Fullscreen to 0,0 with size 1280x1024.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Metacity and is EWMH compliant.
xcommon: You are using metacity.  Disabling aspect ratio hints
xcommon: since most deployed versions of metacity are still broken.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 274: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/user/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'cx8800', card 'UNKNOWN/GENERIC' (bus PCI:0000:01:08.0).
videoinput: Version is 5, capabilities 5000015.
videoinput: Can't get tuner info: Invalid argument
videoinput: Width 720 too high, using 640 instead as suggested by the driver.
videoinput: Maximum input width: 640 pixels.
videoinput: Can't get tuner info: Invalid argument
tvtime: Sampling input at 640 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (79).
xcommon: Window fully obscured, marking window as hidden (192).
xcommon: Window made visible, marking window as visible (200).
tvtime: Cleaning up.
Thank you for using tvtime.



I hope that someone can help me out... thank's!!

---

