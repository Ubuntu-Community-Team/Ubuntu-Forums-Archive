---
title: "Terratec Cinergy HT PCI and remote"
date: 2009-02-18
forum: Hardware
---

### Post by pablo79 on 2009-02-18
Dear all, first at all I'm a beginner so be very patient with me.
I have the TV tuner card in the title that work with philips chipset.
I think the card is recognized automatically by my mythbuntu 8.10because the command dmesg give me some information that seem indicate the card driver is installed correctly (I'm not with my pc so now I'm not able to post the result).
I've tried to see something with xine or vlc but I'm not able to use this programs for this purpose and I still have to read how to insert my tv card in mythtv.

The question is how to test if the card is already installed correctly and if the remote controller works (if yes how to make it working).

Thank you in advance.

Pablo

---

### Post by pablo79 on 2009-02-19
Nobody has an idea to help me?
Please, I'm trying to set the card in mythtv but I would be sure that the card works properly before lost days to try to configure mythtv and at the end discover that the problem is that the card is not installed in the right way.

Thank you, Pablo

Following some command results:

lspci |grep Multimedia
03:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
03:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

dmesg

[CUT]
[   11.792456] Linux video capture interface: v2.00
[   11.982129] saa7130/34: v4l2 driver version 0.2.14 loaded
[   11.983193] saa7134 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.983201] saa7133[0]: found at 0000:03:07.0, rev: 209, irq: 21, latency: 32, mmio: 0xfdcff000
[   11.983208] saa7133[0]: subsystem: 153b:1175, board: Terratec Cinergy HT PCI [card=108,insmod option]
[   11.983217] saa7133[0]: board init: gpio is 40000
[   12.132514] saa7133[0]: i2c eeprom 00: 3b 15 75 11 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   12.132522] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[   12.132529] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 00 06 ff 00 94 02 51 96 2b
[   12.132536] saa7133[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[   12.132543] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 32 15 10 fd 79 44 9f c2 8f
[   12.132550] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132556] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132563] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132570] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132577] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132583] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132590] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132597] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132604] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132611] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.132618] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.244110] tuner' 1-004b: chip found @ 0x96 (saa7133[0])
[   12.332511] tda829x 1-004b: setting tuner address to 60
[   12.408514] tda829x 1-004b: type set to tda8290+75a
[   16.245278] saa7133[0]: registered device video0 [v4l2]
[   16.245411] saa7133[0]: registered device vbi0
[   16.325952] saa7134 ALSA driver for DMA sound loaded
[   16.325979] saa7133[0]/alsa: saa7133[0] at 0xfdcff000 irq 21 registered as card -2
[   16.464583] DVB: registering new adapter (saa7133[0])
[   16.464588] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   16.536015] tda1004x: setting up plls for 48MHz sampling clock
[   17.044314] lp0: using parport0 (interrupt-driven).
[CUT]
[   42.706975] lirc_dev: IR Remote Control driver registered, major 61 
[   42.816033] ivtv:  Start initialization, version 1.4.0
[   42.816071] ivtv:  End initialization

---

### Post by IcarusR on 2009-02-20
A good site with instructions how to install & configure, as well as having useful links 
[http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")

This page tells how to test a db tv card 
[http://parker1.co.uk/mythtv_dvb.php]("http://parker1.co.uk/mythtv_dvb.php")

Try using [www.google.com]("www.google.com") thats how I found the above site when I set up MythTV

---

### Post by pablo79 on 2009-02-21
Thank you IcarusR, I'll read the links you suggest me.
Do you have this card or do you now if the remote works under linux? I've searched information but I didn't find it.
Thank you again,
  Pablo

---

### Post by pablo79 on 2009-02-23
Dear all,
I've read the guide suggested by IcarusR ([http://parker1.co.uk/mythtv_dvb.php]("Testing your DVB Card")) and this is the result of the command **tzap**
status 1f | signal 9b9b | snr fefe | ber 000000a2 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 9c9c | snr fefe | ber 00000092 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 9b9b | snr fefe | ber 000000d2 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 9b9b | snr fefe | ber 0000005c | unc 00000000 | FE_HAS_LOCK
It seems the card works.
But when I try to see the tv with mplayer or xine as suggested in the guide I cannot see anything.
With mplayer I have this result:
dvbstream -o -ps 600 601 -qam 16 -cr 3_4 | mplayer -

dvbstream v0.6 - (C) Dave Chapman 2001-2004
Released under the GPL.
Latest version available from [http://www.linuxstb.org/](http://www.linuxstb.org/)
dvbstream will stop after -1 seconds (71582788 minutes)
Output to stdout
Streaming 2 streams
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) Dual Core Processor 5050e (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...


and nothing append.

With xine:
dvbstream -o -ps 600 601 -qam 16 -cr 3_4 | xine stdin://mpeg2

dvbstream v0.6 - (C) Dave Chapman 2001-2004
Released under the GPL.
Latest version available from [http://www.linuxstb.org/](http://www.linuxstb.org/)
dvbstream will stop after -1 seconds (71582788 minutes)
Output to stdout
Streaming 2 streams
Questo è xine (X11 gui) - un riproduttore video libero v0.99.6cvs.
(c) 2000-2007 Team di xine.

xine starts but the window is black

What's wrong?

Thank you for your help. Paoblo

---

### Post by pablo79 on 2009-03-03
Dear all,
   after a lot of test and a mythbuntu reinstallation the dvb card works correctly in Kaffeine :P and more or less in mythtv :(. For now this part is enough, I will work to see all the channels in mythtv.
Someone know if the remote works on this card? Please help me.

I've read lot of guide how to set lirc but all start with read the event number in cat /proc/bus/input/devices
But it seems I've not the remote control device in my system.

Thank you in advance,
   Pablo

---

