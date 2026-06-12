---
title: "D-link Webcam found once then re-installed, can't find again"
date: 2008-11-11
forum: General Help
---

### Post by Neo_The_User on 2008-11-11
OK I have been using Ubuntu 8.10 since it came out, no problems with my webcam until I re-installed my system.

```

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

```

```

ls /dev/video*
/dev/video0

```

Camera will not actually work. Applications > Graphics > Cheese 2.24 > Camera not found

Applications > Graphics > Camorama > Could not connect to video device (/dev/video0). Please check connection.

Facebook / flash player won't detect it either. It worked fine with Ubuntu 8.10 until I re-installed it about 10 minutes ago. I don't know why but I did. Any suggestions? btw, I re-installed Ubuntu with rhe camera pluged in and left in plugged in the whole time during the last 3 reboots. Still no dice. I have installed many many applications to see if I needed any special software, still didn't work. What is wrong? It worked before. The green light on the camera is on.

This is what I pulled out of my /dev/video0 file / de-compiled

```

free(): invalid next size (fast): 0x090bc248 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7fb33f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7fb5456]
/lib/tls/i686/cmov/libc.so.6[0xb7f6d0c8]
/lib/tls/i686/cmov/libc.so.6[0xb7f6d151]
/lib/tls/i686/cmov/libc.so.6[0xb7f6d151]
/lib/tls/i686/cmov/libc.so.6[0xb7f6d08a]
/lib/tls/i686/cmov/libc.so.6[0xb7f6d08a]
/lib/tls/i686/cmov/libc.so.6[0xb7f6d08a]
/lib/tls/i686/cmov/libc.so.6[0xb7f6b0e2]
/lib/tls/i686/cmov/libc.so.6[0xb7f6a8c1]
/lib/tls/i686/cmov/libc.so.6(dcgettext+0x43)[0xb7f69613]
/lib/tls/i686/cmov/libc.so.6(__strerror_r+0x4e)[0xb7fbb1ae]
/lib/tls/i686/cmov/libc.so.6[0xb802465f]
/lib/tls/i686/cmov/libc.so.6[0xb8024843]
/lib/tls/i686/cmov/libc.so.6(error+0x59)[0xb8024a89]
cat[0x8049bdb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7f5a685]
cat[0x8048d31]
======= Memory map: ========
090b4000-090d5000 rw-p 090b4000 00:00 0          [heap]
b7cf1000-b7cfe000 r-xp 00000000 08:02 4227134    /lib/libgcc_s.so.1
b7cfe000-b7cff000 r--p 0000c000 08:02 4227134    /lib/libgcc_s.so.1
b7cff000-b7d00000 rw-p 0000d000 08:02 4227134    /lib/libgcc_s.so.1
b7d00000-b7d21000 rw-p b7d00000 00:00 0 
b7d21000-b7e00000 ---p b7d21000 00:00 0 
b7e23000-b7e62000 r--p 00000000 08:02 575462     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7e62000-b7f43000 r--p 00000000 08:02 575461     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7f43000-b7f44000 rw-p b7f43000 00:00 0 
b7f44000-b809c000 r-xp 00000000 08:02 4244825    /lib/tls/i686/cmov/libc-2.8.90.so
b809c000-b809e000 r--p 00158000 08:02 4244825    /lib/tls/i686/cmov/libc-2.8.90.so
b809e000-b809f000 rw-p 0015a000 08:02 4244825    /lib/tls/i686/cmov/libc-2.8.90.so
b809f000-b80a3000 rw-p b809f000 00:00 0 
b80a7000-b80a8000 r--p 00000000 08:02 575467     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b80a8000-b80a9000 r--p 00000000 08:02 575470     /usr/lib/locale/en_US.utf8/LC_TIME
b80a9000-b80aa000 r--p 00000000 08:02 575465     /usr/lib/locale/en_US.utf8/LC_MONETARY
b80aa000-b80ab000 r--p 00000000 08:02 575471     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b80ab000-b80ac000 r--p 00000000 08:02 575468     /usr/lib/locale/en_US.utf8/LC_PAPER
b80ac000-b80ad000 r--p 00000000 08:02 575466     /usr/lib/locale/en_US.utf8/LC_NAME
b80ad000-b80ae000 r--p 00000000 08:02 575460     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b80ae000-b80af000 r--p 00000000 08:02 575469     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b80af000-b80b0000 r--p 00000000 08:02 575464     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b80b0000-b80b7000 r--s 00000000 08:02 1982707    /usr/lib/gconv/gconv-modules.cache
b80b7000-b80b8000 r--p 00000000 08:02 575463     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b80b8000-b80b9000 rw-p b80b8000 00:00 0 
b80b9000-b80d3000 r-xp 00000000 08:02 4227091    /lib/ld-2.8.90.so
b80d3000-b80d4000 r-xp b80d3000 00:00 0          [vdso]
b80d4000-b80d5000 r--p 0001a000 08:02 4227091    /lib/ld-2.8.90.so
b80d5000-b80d6000 rw-p 0001b000 08:02 4227091    /lib/ld-2.8.90.so
bfec1000-bfed6000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

---

### Post by Neo_The_User on 2008-11-12
No matter what I do, I can't get the webcam working again. ...bump.

Please help.

---

### Post by Neo_The_User on 2008-11-24
Here is what I got from dmesg.

```

[ 7341.704018] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 7341.873740] usb 3-2: configuration #1 chosen from 1 choice
[ 7342.033970] Linux video capture interface: v2.00
[ 7342.054231] ov511: USB OV511+ video device found
[ 7342.055604] ov511: model: Generic Camera (no ID)
[ 7342.167555] ov511: i2c write retries exhausted
[ 7342.353527] ov511: Sensor is an OV6620
[ 7342.628735] ov511: Device at usb-0000:00:10.1-2 registered to minor 0
[ 7342.630064] usbcore: registered new interface driver ov511
[ 7342.631122] ov511: v1.64 for Linux 2.5 : ov511 USB Camera Driver

```

---

