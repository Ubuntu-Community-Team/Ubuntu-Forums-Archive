---
title: "Elgato EyeTV Hybrid problem"
date: 2012-07-16
forum: Hardware
---

### Post by markosjal on 2012-07-16
I have an elgato EyeTV Hybrid. Same As the Hauppauge 950/980, however the Mac version. I can no longer tune channels on the Mac and I think this happened as a result of trying to run it on linux.

lsusb reports it as:
Bus 001 Device 002: ID 2040:6513 Hauppauge WinTV HVR-980

According to this and other pages, that is correct
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950)

This is an NTSC/ATSC model however I think somehow the firmware got messed up and it thinks it is the PAL/DVB version.

I think it has a personality disorder

How can I correct this?

Thanks


 doing grep -i dvb /var/log/messages yields this:

Jul 16 19:15:50 GayGuey-Mint kernel: [  354.218838] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
Jul 16 19:15:52 GayGuey-Mint kernel: [  356.552215] DVB: registering new adapter (em28xx #0)
Jul 16 19:15:52 GayGuey-Mint kernel: [  356.552227] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
Jul 16 19:15:52 GayGuey-Mint kernel: [  356.553848] em28xx #0: Successfully loaded em28xx-dvb
Jul 16 19:15:52 GayGuey-Mint kernel: [  356.553871] Em28xx: Initialized (Em28xx dvb Extension) extension
Jul 16 19:29:56 GayGuey-Mint kernel: [ 1200.584695]  [<f9709c55>] dvb_dmxdev_release+0xa5/0x100 [dvb_core]
Jul 16 19:29:56 GayGuey-Mint kernel: [ 1200.584724]  [<f9730040>] unregister_dvb+0x40/0x70 [em28xx_dvb]
Jul 16 19:29:56 GayGuey-Mint kernel: [ 1200.584735]  [<f9730093>] dvb_fini+0x23/0x40 [em28xx_dvb]
Jul 16 19:31:56 GayGuey-Mint kernel: [ 1320.584283]  [<f9709c55>] dvb_dmxdev_release+0xa5/0x100 [dvb_core]
Jul 16 19:31:56 GayGuey-Mint kernel: [ 1320.584314]  [<f9730040>] unregister_dvb+0x40/0x70 [em28xx_dvb]
Jul 16 19:31:56 GayGuey-Mint kernel: [ 1320.584327]  [<f9730093>] dvb_fini+0x23/0x40 [em28xx_dvb]
Jul 16 19:33:56 GayGuey-Mint kernel: [ 1440.584283]  [<f9709c55>] dvb_dmxdev_release+0xa5/0x100 [dvb_core]
Jul 16 19:33:56 GayGuey-Mint kernel: [ 1440.584314]  [<f9730040>] unregister_dvb+0x40/0x70 [em28xx_dvb]
Jul 16 19:33:56 GayGuey-Mint kernel: [ 1440.584327]  [<f9730093>] dvb_fini+0x23/0x40 [em28xx_dvb]
Jul 16 19:35:56 GayGuey-Mint kernel: [ 1560.584275]  [<f9709c55>] dvb_dmxdev_release+0xa5/0x100 [dvb_core]
Jul 16 19:35:56 GayGuey-Mint kernel: [ 1560.584306]  [<f9730040>] unregister_dvb+0x40/0x70 [em28xx_dvb]
Jul 16 19:35:56 GayGuey-Mint kernel: [ 1560.584319]  [<f9730093>] dvb_fini+0x23/0x40 [em28xx_dvb]
Jul 16 19:37:56 GayGuey-Mint kernel: [ 1680.584312]  [<f9709c55>] dvb_dmxdev_release+0xa5/0x100 [dvb_core]
Jul 16 19:37:56 GayGuey-Mint kernel: [ 1680.584356]  [<f9730040>] unregister_dvb+0x40/0x70 [em28xx_dvb]
Jul 16 19:37:56 GayGuey-Mint kernel: [ 1680.584376]  [<f9730093>] dvb_fini+0x23/0x40 [em28xx_dvb]
Jul 16 19:39:56 GayGuey-Mint kernel: [ 1800.584282]  [<f9709c55>] dvb_dmxdev_release+0xa5/0x100 [dvb_core]
Jul 16 19:39:56 GayGuey-Mint kernel: [ 1800.584313]  [<f9730040>] unregister_dvb+0x40/0x70 [em28xx_dvb]
Jul 16 19:39:56 GayGuey-Mint kernel: [ 1800.584326]  [<f9730093>] dvb_fini+0x23/0x40 [em28xx_dvb]
Jul 16 19:46:15 GayGuey-Mint kernel: [   66.419580] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
Jul 16 19:46:18 GayGuey-Mint kernel: [   68.702462] DVB: registering new adapter (em28xx #0)
Jul 16 19:46:18 GayGuey-Mint kernel: [   68.702473] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
Jul 16 19:46:18 GayGuey-Mint kernel: [   68.705111] em28xx #0: Successfully loaded em28xx-dvb
Jul 16 19:46:18 GayGuey-Mint kernel: [   68.705135] Em28xx: Initialized (Em28xx dvb Extension) extension
Jul 16 19:52:56 GayGuey-Mint kernel: [  467.030074] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
Jul 16 19:55:09 GayGuey-Mint kernel: [  600.580744]  [<f8bdf5e3>] dvb_init+0x73/0x650 [em28xx_dvb]
Jul 16 19:56:55 GayGuey-Mint kernel: [   22.607038] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
Jul 16 19:56:58 GayGuey-Mint kernel: [   25.451847] DVB: registering new adapter (em28xx #0)
Jul 16 19:56:58 GayGuey-Mint kernel: [   25.451857] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
Jul 16 19:56:58 GayGuey-Mint kernel: [   25.452940] em28xx #0: Successfully loaded em28xx-dvb
Jul 16 19:56:58 GayGuey-Mint kernel: [   25.452952] Em28xx: Initialized (Em28xx dvb Extension) extension

---

