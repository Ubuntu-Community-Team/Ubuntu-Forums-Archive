---
title: "Gateway Laptop Sound"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by browndog on 2006-04-14
This is one newbie who is definitely loving Ubuntu but could really use some help with the sound problem I'm having.  I have a Gateway 4540GZ laptop with Breezy installed.  Everything works fine, except that no matter what I do I cannot get any sound out of this thing.  I've already checked the Wiki and have carried out the sound troubleshooting instructions to the absolute best of my ability (carefully followed each line).  I've unmuted the sound and turned the volume all the way up in every place I can find.  I've tried selecting the ALSA, ESD, and OSS Multimedia Systems (each one in turn) from System --> Preferences --> Multimedia Systems Selector but still no dice.

lspci gives me the following:

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

aplay -l gives me the following output:

aplay -l output:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help anyone can give would be tremendously appreciated.

BD

---

### Post by andlinux21 on 2006-04-14
you may want to try using modprobe sb io=0x220 irq=5 dma=1 dma16=5 mpu_io=0x330 it worked for me when i had problems with my laptop i posted long ago about my troubles

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=browndog]This is one newbie who is definitely loving Ubuntu but could really use some help with the sound problem I'm having.  I have a Gateway 4540GZ laptop with Breezy installed.  Everything works fine, except that no matter what I do I cannot get any sound out of this thing.  I've already checked the Wiki and have carried out the sound troubleshooting instructions to the absolute best of my ability (carefully followed each line).  I've unmuted the sound and turned the volume all the way up in every place I can find.  I've tried selecting the ALSA, ESD, and OSS Multimedia Systems (each one in turn) from System --> Preferences --> Multimedia Systems Selector but still no dice.

lspci gives me the following:

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

aplay -l gives me the following output:

aplay -l output:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help anyone can give would be tremendously appreciated.

BD[/QUOTE]
I had the same problem with my gateway laptop ! I had no sound at all. Nothing was muted either. I fixed the sound problem by upgrading my kernel to 2.16.6. Go under volume and make sure every sound device is enabled/not muted.

---

### Post by browndog on 2006-04-15
When I try running your command I get the following error message:

FATAL: Error inserting sb (/lib/modules/2.6.12-9-386/kernel/sound/oss/sb.ko): No such device

Any ideas?

---

### Post by nyara on 2006-04-30
BUMP

I'm having this same problem.  Anybody know what to do?

---

### Post by AlainM on 2006-09-06
I'm not running Ubuntu, but Fedora Core 5. I don't think it matters; my 4540GZ is happily playing music. Open Volume Control, go to Preferences, and select all tracks to be visible. Then go to the Switches tab, and UNCHECK External Amplifier.

It may not work right away, I remember I had to reboot and play with External Amplifier a couple of times before it worked. But now it works!

-- alain.

---

### Post by sdobbers on 2007-02-10
My sound card is also, Intel 82801DB-ICH4.  I'm having this same problem too, no sound at all.

---

### Post by ljlolel on 2007-03-16
Unchecking External Amplifier works beatifully for me!!!

---

### Post by damonc on 2007-04-25
> **AlainM said:**
> Then go to the Switches tab, and UNCHECK External Amplifier.

This worked for me too, thanks for the advice.

---

### Post by craz_mofo on 2007-05-08
Unchecking "External Amplifier" worked for me too, and I have a Gateway 7320GZ with Intel 82801DB-ICH4.  AlainM, you're a freaking genius! :lolflag:

---

### Post by topgrip on 2007-05-13
THANK YOU !!! THANK YOU !!! i was about to loose hope and start looking at windows again, but the External Amp uncheck finally gave me sound !!! now I can finally start using the power of Ubuntu ..... once I install beryl  :)

---

