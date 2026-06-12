---
title: "ubuntu server and sound"
date: 2008-07-31
forum: Hardware
---

### Post by ciuci on 2008-07-31
well i would like to install sound on an ubuntu-server system (seriously don't ask me why, and don't tell me to use the desktop version, if you have any information on **how to do it**, i would greatly appreciate) and don't have any idea where to begin... i tried apt-getting some packages that contain "alsa" in their name, but that has brought me nowhere ... i searched a lot of places but didn't find anything :( ... please help me!


*note:i have a realtek ac`97 soundcard integrated into a via chipset (gigabyte motherboard with amd athlon xp processor)

---

### Post by donaldvr on 2008-08-19
I have the same issue.  I have an ubuntu fileserver.  I want to use it to play a looped promotional mp3 file for customers who are on hold.  There has to be a way to do this.

---

### Post by cariboo on 2008-08-19
We need a lot more info then either of you have given, if your chipset is support setting up sound takes no time at all.
Please post the output of:

```
lspci
```

Once we have this inforamtion, we should be able to help you get sound working.

Jim

---

### Post by unbkbl on 2008-09-01
Hello, I've the same problem and the same soundcard.
I've installed Ubuntu server because i don't really like gnome (too heavy for my 512 Mg in RAM) and I'm trying Enlightenment e17 (really beautiful).
I tried to manually install sound like this:

```
apt-get install alsa-base alsa-utils alsa-tools libasound2
```
But it doesn't work. I've turned up the volume in the alsamixer... and nothing

so..

My lspi output is this:

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
daniel@lab:~$ 
```
My aplay -l output is this:

```
daniel@lab:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

My lspci -v output is this:

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at b0040800 (32-bit, non-prefetchable) [size=512]
        Memory at b0040400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
```

I have done the procedure in the first code tag installing sound in Debian a few days ago it and worked!

Any Ideas?
:confused:

---

