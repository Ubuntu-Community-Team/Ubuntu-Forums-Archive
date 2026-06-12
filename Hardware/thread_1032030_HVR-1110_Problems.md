---
title: "HVR-1110 Problems"
date: 2009-01-05
forum: Hardware
---

### Post by seanlano on 2009-01-05
Hi,
I have a PC which came with Windows Vista, and a TV tuner card in it. I have since dual-booted it with Ubuntu (8.10, latest kernel), and have been trying for ages to get the stupid tuner to work. [_In this post_]("http://ubuntuforums.org/showthread.php?t=947228") I found out that it was a Hauppauge HVR-1110. I have tried a few tutorials on how to install it, the most successful being [_this one_]("http://en.ubuntuforums.org/showthread.php?t=623126&page=2"). I couldn't get the perl script to extract the firmware, so I did it manually by downloading the file from the website in the script then going through and finding the /TT_PCI_2.19h_28_11_2006/software/OEM/PCI/App/**ttlcdacc.dll** and naming it to **dvb-fe-tda10046.fw**, which is what the script appeared to do. I then put it in the /lib/firmware/ folder. I re-booted the PC and then tried the scan in the tutorial, which partially worked, and I could even get MythTV to show me some TV, and it worked fine (although I only had ABC channels, I guess it needed a bit more tweaking). I was given a glimpse of hope, but then it was torn away. lol. I hibernated the PC and went to bed, then the next time I tried to use it, the scan program aid the card was locked or in use or something, and Myth didn't give any output (but the Over-the-air EPG still worked...). I re-booted, then it completely locked up at:[I]
Loading the saved-state of the serial devices...
[29.404008] tda1004x timeout waiting for DSP ready[/I]
I had to use a LiveCD to remove the dvb-fe-tda10046.fe from it's location to get the computer to function again. Since then I cannot get it to work. I have tried looking for alternate sources for the driver, but it is hard to come by. I went to the Hauppauge website and got a windows driver in a .zip file, but I have no idea which file to use, or even if it will work. There is a file called **HCW713XMV.dll** in the .zip, which is the only 32-bit dll in there. 

Could this work? (if I rename it)
What else can I try?
:confused:
thank you in advance

---

### Post by seanlano on 2009-01-06
Ok, I renamed the file and put it in. It sort of worked, the computer booted fine. But the now when I run ```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne > ~/.tzap/channels.conf
``` I get: ```
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

``` I also got this error using the included firmware in ubuntu. The card is definitely detected, dmesg says: ```
[   20.879846] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.880907] saa7134 0000:03:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.880916] saa7133[0]: found at 0000:03:02.0, rev: 209, irq: 17, latency: 84, mmio: 0xefbff000
[   20.880924] saa7133[0]: subsystem: 0070:6700, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
[   20.880935] saa7133[0]: board init: gpio is 400000
[   21.032012] saa7133[0]: i2c eeprom 00: 70 00 00 67 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   21.032026] saa7133[0]: i2c eeprom 10: ff ff ff 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[   21.032038] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 33 88 ff 00 a3 ff ff ff ff
[   21.032049] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.032061] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 60 ff ff ff ff ff ff
[   21.032072] saa7133[0]: i2c eeprom 50: ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   21.032084] saa7133[0]: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   21.032095] saa7133[0]: i2c eeprom 70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   21.032106] saa7133[0]: i2c eeprom 80: 84 09 00 04 20 77 00 40 a9 5a 12 f0 73 05 29 00
[   21.032118] saa7133[0]: i2c eeprom 90: 84 08 00 06 e7 07 01 00 94 18 89 72 07 70 73 09
[   21.032130] saa7133[0]: i2c eeprom a0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 10 01 72
[   21.032141] saa7133[0]: i2c eeprom b0: 11 ff 79 bf 00 00 00 00 00 00 00 00 00 00 00 00
[   21.032153] saa7133[0]: i2c eeprom c0: 84 09 00 04 20 77 00 40 a9 5a 12 f0 73 05 29 00
[   21.032164] saa7133[0]: i2c eeprom d0: 84 08 00 06 e7 07 01 00 94 18 89 72 07 70 73 09
[   21.032176] saa7133[0]: i2c eeprom e0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 10 01 72
[   21.032187] saa7133[0]: i2c eeprom f0: 11 ff 79 bf 00 00 00 00 00 00 00 00 00 00 00 00
[   21.081085] nvidia: module license 'NVIDIA' taints kernel.
[   21.424074] tuner' 0-004b: chip found @ 0x96 (saa7133[0])
[   21.426933] tveeprom 0-0050: Hauppauge model 67559, rev B1B4, serial# 1202857
[   21.426937] tveeprom 0-0050: MAC address is 00-0D-FE-12-5A-A9
[   21.426940] tveeprom 0-0050: tuner model is Philips 8275A (idx 114, type 4)
[   21.426943] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
[   21.426946] tveeprom 0-0050: audio processor is SAA7131 (idx 41)
[   21.426949] tveeprom 0-0050: decoder processor is SAA7131 (idx 35)
[   21.426951] tveeprom 0-0050: has radio
[   21.426953] saa7133[0]: hauppauge eeprom: model=67559
[   21.516008] tda829x 0-004b: setting tuner address to 61
[   21.608009] tda829x 0-004b: type set to tda8290+75a
[   25.464327] saa7133[0]: registered device video0 [v4l2]
[   25.464380] saa7133[0]: registered device vbi0
[   25.464432] saa7133[0]: registered device radio0
[   25.528061] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.528071] nvidia 0000:01:00.0: setting latency timer to 64
[   25.528177] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   25.550024] saa7134 ALSA driver for DMA sound loaded
[   25.550055] saa7133[0]/alsa: saa7133[0] at 0xefbff000 irq 17 registered as card -2
[   25.648086] DVB: registering new adapter (saa7133[0])
[   25.648090] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   25.720007] tda1004x: setting up plls for 48MHz sampling clock

```

What could be causing the resource to be busy?

---

### Post by antebe on 2009-01-07
Hello, 
I am a total beginner myself, so I probably cannot help you if you get stuck, but I got started fairly easily with Mythbuntu 8.10 and a HVR-1110 card using this link 
[http://forums.debian.net/viewtopic.php?p=130129](http://forums.debian.net/viewtopic.php?p=130129) for the TV part.

If you want to have the remote as well you should look at this thread instead:
[http://ubuntuforums.org/showthread.php?t=914128](http://ubuntuforums.org/showthread.php?t=914128)

I hope you get lucky! :D

---

### Post by seanlano on 2009-01-07
ok, thanks a bunch. 
would you be able to upload your dvb-fe-tda10046.fw to the forum? I'm having difficulty getting a copy. Thanks!

---

### Post by seanlano on 2009-08-30
Installed Interpid and it worked fine OOTB. Same for Jaunty.

---

