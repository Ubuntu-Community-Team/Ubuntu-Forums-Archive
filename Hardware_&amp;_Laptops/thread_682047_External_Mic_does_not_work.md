---
title: "External Mic does not work"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by Ub1476 on 2008-01-29
Hi, my external mic does not work. No sound at all except for XP. I've tested it on XP 64 (barely any sound), Vista 32(no sound), Ubuntu 32 (no sound), and XP 32 (clear good sound). Is it a driver problem?

Here's hardware:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

---

### Post by Ub1476 on 2008-01-30
bump

---

### Post by cdtech on 2008-01-30
What happens when you run:
```
arecord -f cd -D hw:0,0 -d 20 test.wav
```

Does it record at all? or what message do you get?

---

### Post by Ub1476 on 2008-01-30
Thanks for reply.

When I play the file, there's still no sound.. I believe the terminal output is as it is supposed to be:
```
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```

I played around a little in the volume control, still no sound, but the "buzz" which comes from the file (I recorded), has greatly increased.

So obviously the microphone is spotted, but can't record anything?

---

### Post by cdtech on 2008-01-30
Have you tried to select a capture device in the alsamixer?

Sounds like this is the problem.

This is my alsamixer when I press f5 I get "Playback Capture [All]" . Here you can select your Intmic or LineIn as your capture.

[ATTACH]58087[/ATTACH]

---

### Post by Ub1476 on 2008-02-01
I've been in the Alsamixer (terminal), checking all controls (F1, F2, F3 etc..), but still it doesn't work.. Do I have to "enable" it somehow?

---

### Post by Ub1476 on 2008-02-03
bump

---

### Post by cdtech on 2008-02-03
Did you press f5 and use your arrow keys to highlight the LineIn or IntMic and select with your space bar to select as a capture device?

---

### Post by Ub1476 on 2008-03-03
Hi, sorry for the late reply.. Here's a picture of alsamixer, F5:

---

### Post by Ub1476 on 2008-03-04
bump

---

