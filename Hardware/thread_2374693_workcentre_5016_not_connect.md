---
title: "workcentre 5016 not connect"
date: 2017-10-18
forum: Hardware
---

### Post by albag on 2017-10-18
XUBUNTU 16.04 64bit 

Xerox workcentre 5016 not connect
[COLOR=#000000][FONT=&amp]
sudo sane-find-scanner [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]found USB scanner (vendor=0x0924 [Xerox Co,.], product=0x4271 [WorkCentre 5016/5020]) at libusb:001:004 [/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]sudo scanimage -L[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]No scanners were identified.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]root@alpc:/etc# ldd /usr/lib/sane/libsane-xrwc5020.so.1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]linux-gate.so.1 => (0xf77f2000) [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]libsane.so.1 => /usr/lib/i386-linux-gnu/libsane.so.1 (0xf7798000) [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]libusb-0.1.so.4 => /lib/i386-linux-gnu/libusb-0.1.so.4 (0xf778e000) [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf75d7000) [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf75d2000) [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/lib/ld-linux.so.2 (0x56644000) [/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]sudo strace scanimage -L  
[/FONT][/COLOR]Errors I do not see
Help!

---

