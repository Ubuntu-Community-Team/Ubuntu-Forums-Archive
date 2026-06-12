---
title: "Hercules SMART TV 3"
date: 2008-12-17
forum: Hardware
---

### Post by qinnie on 2008-12-17
Hi there

I'm hoping to find some help to get my **Hercules SMART TV 3** card working on ubuntu. Right now, I get no sound nor image. I did already a lot of research and here are my results:

Some info from the card:
[LIST]
[*]HERCULES SMART TV 3 is mentioned on the card
[*]there is a chip with SAA7130hl on it
[*]dmesg can detect the card on booting
[/LIST]

Some info from my computer:
[LIST]
[*]Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
[*]Running Ubuntu Intrepid
[/LIST]

My card is not on the list ([http://en.gentoo-wiki.com/index.php?title=HARDWARE_saa7134]("http://en.gentoo-wiki.com/index.php?title=HARDWARE_saa7134"))
although it is mentioned on this page ([http://www.linuxtv.org/v4lwiki/index.php/Saa713x_devices]("http://www.linuxtv.org/v4lwiki/index.php/Saa713x_devices"))

Showing all my PCI devices:
```

lspci

...
02:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
...

```

On that Gentoo page is a code snippet to try autodetecting the card:

```

lsmod |grep ^saa|cut -d " " -f 1|xargs rmmod - ; modprobe saa7134 i2c_scan=1

```
with results from dmesg:
```

[ 5285.562763] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 5285.563412] saa7130[0]: found at 0000:02:08.0, rev: 1, irq: 17, latency: 64, mmio: 0xfcfdfc00
[ 5285.563427] saa7130[0]: subsystem: 1131:233c, board: UNKNOWN/GENERIC [card=0,autodetected]
[ 5285.563443] saa7130[0]: board init: gpio is 1d81ff
[ 5285.680013] All bytes are equal. It is not a TEA5767
[ 5285.680133] tuner' 0-0060: chip found @ 0xc0 (saa7130[0])
[ 5285.688022] tuner' 0-0061: chip found @ 0xc2 (saa7130[0])
[ 5285.736016] saa7130[0]: i2c eeprom 00: 31 11 3c 23 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[ 5285.736032] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[ 5285.736044] saa7130[0]: i2c eeprom 20: 41 3c 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736056] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736068] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736080] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736092] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736104] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736116] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736128] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736140] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736152] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736164] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736176] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736189] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.736201] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5285.780016] saa7130[0]: i2c scan: found device @ 0xa0  [eeprom]
[ 5285.792022] saa7130[0]: i2c scan: found device @ 0xc0  [tuner (analog)]
[ 5285.800015] saa7130[0]: i2c scan: found device @ 0xc2  [???]
[ 5285.811406] saa7130[0]: registered device video0 [v4l2]
[ 5285.811879] saa7130[0]: registered device vbi0
[ 5285.904971] saa7134 ALSA driver for DMA sound loaded
[ 5285.905287] saa7130[0]/alsa: saa7130[0] at 0xfcfdfc00 irq 17 registered as card -2


```

Tvtime-scanner says
```

Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.


    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.


```

Of course I can start trying all different cards with all different kind of tuners, but hey, that will take ages...

I really hope someone here can help me, I would be glad!

---

