---
title: "Grrrrrrr PCTV Hybrid Pro PCI Remote"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by michaelrc on 2008-01-07
Has any one got his to work....... the remote ?

Dmesg:
saa7133[0]: subsystem: 11bd:002f, board: Pinnacle PCTV 310i [card=101,autodetected]
[   32.615531] saa7133[0]: board init: gpio is 600e000
[   32.754466] input: Pinnacle PCTV as /class/input/input3
[   32.754504] ir-kbd-i2c: Pinnacle PCTV detected at i2c-1/1-0047/ir0 [saa7133[0]]
[   32.806156] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   32.806168] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2f 95 24 ff ff
[   32.806178] saa7133[0]: i2c eeprom 20: 01 2c 01 23 23 01 04 30 98 ff 00 e7 ff 21 00 c2
[   32.806187] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff 15 0e 6c a3 eb 04 40 12 f7
[   32.806197] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.806207] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.806217] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.806226] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.933825] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   32.989688] tuner 1-004b: setting tuner address to 61
[   33.029591] tuner 1-004b: type set to tda8290+75a
[   34.418242] tuner 1-004b: setting tuner address to 61
[   34.458145] tuner 1-004b: type set to tda8290+75a
[   35.475692] Pinnacle PCTV: unknown key: key=0x01 raw=0x01 down=1
[   35.583431] Pinnacle PCTV: unknown key: key=0x01 raw=0x01 down=0
[   35.817954] saa7133[0]: registered device video0 [v4l2]
[   35.818097] saa7133[0]: registered device vbi0
[   35.818221] saa7133[0]: registered device radio0
[   35.878907] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
[   35.879052] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   35.895233] saa7134 ALSA driver for DMA sound loaded
[   35.895266] saa7133[0]/alsa: saa7133[0] at 0xdfffb800 irq 20 registered as card -2
[   36.194494] DVB: registering new adapter (saa7133[0]).
[   36.194501] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   36.265787] tda1004x: setting up plls for 48MHz sampling clock
[   36.549105] tda1004x: found firmware revision 20 -- ok

Start at.

sudo lircd --nodaemon
accepted new client on /dev/lircd

Open new terminal
irw

And on the other terninal i got
lircd(userspace) ready
lircd-0.8.2[5021]: accepted new client on /dev/lircd
lircd-0.8.2[5021]: could not get file information for /dev/lirc
lircd-0.8.2[5021]: default_init(): No such file or directory
lircd-0.8.2[5021]: caught signal

ls -l /dev/li*
srw-rw-rw- 1 root root 0 2008-01-07 19:49 /dev/lircd

So i start my lirc again /etc/init.d/lirc start

and try

ps -aux

/usr/sbin/lircd --driver=pinsys --device=/dev/ttyS0

Help me [-o<

---

