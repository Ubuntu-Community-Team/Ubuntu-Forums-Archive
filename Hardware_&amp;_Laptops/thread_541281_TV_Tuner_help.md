---
title: "TV Tuner help"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by elias85 on 2007-09-02
my tv card is V-STREAM (with lspci i get 02:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05) how can i watch tv on my pc? pls help!

---

### Post by Jose Catre-Vandis on 2007-09-02
From what I have read, you have a hybrid card (DVB & Analog). If its only analog, just work with TVTime, if only dvb then work with Kaffeine, if both  :)

First off, install TV Time and Kaffeine
```
sudo apt-get install tvtime kaffeine
```
next run this code in a terminal:
```
sudo modprobe cx88_dvb
```

For this to work everytime, add the line cx88_dvb to your /etc/modules file:
```
sudo nano /etc/modules

add cx88_dvb to bottom of list

CTRL+X, then Y, then Enter
```

Analog:
Run tvtime (Applications>Sound & Video>TvTime)
hopefully it will present a menu from which you can start to scan for channels - be patient. If all goes well, you have analog tv working.

Dvb:
Run Kaffeine (Applications>Sound&Video>Kaffeine)
If the modules are loaded up you should have six options, one being Digital TV. Click on it, then click on DVB in the File menu and choose Configure DVB. Choose the region/transmitter nearest you and click OK. Then click on the little black TV (tooltip "Channels") top left (below "View"). Click on "Start Scan" and you should get channels. Copy them across and then watch dvb tv.

---

### Post by elias85 on 2007-09-10
sudo modprobe cx88_dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device


what can i do?
lspci --->


lspci
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

---

### Post by Arcsis on 2007-09-13
I got a similar error after using the **_sudo modprobe cx88_dvb_** command, following the directions in the previous post.

FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

I have the Leadtek WinFast TV 2000 Expert TV&FM Tuner card if that makes a difference. :)

---

### Post by elias85 on 2007-09-13
Any help?

---

### Post by viciouslime on 2007-09-13
> **Arcsis said:**
> I got a similar error after using the **_sudo modprobe cx88_dvb_** command, following the directions in the previous post.

FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

I have the Leadtek WinFast TV 2000 Expert TV&FM Tuner card if that makes a difference. :)

It does, the command given there is to load the connexant TV card driver. There is a bug in the feisty kernel that stops it being loaded automatically so you have to load it manually.

If you don't have a card that uses a connexant chipset, you DON'T need to run this command. I don't think that driver is for ALL connexant cards either... I know the Hauppauge Nova T uses that driver, but i can't remember its exact chipset.

Anyway if that command fails it means that driver isn't for your card and the chances are the correct driver has already been loaded, unless your card isn't supported by linux.

This means you can skip this step completely. If you can't get TVTime of Kaffine to work, MythTV has a MUCH better scanning thing. However, it is a little more diffiult to set-up, if you follow the guide on the ubuntu wiki however, you shouldn't have a problem.

Hope that helps :D

---

### Post by viciouslime on 2007-09-13
I've just used ssh to connect to my machine with a Hauppauge Nova-T in it, I ran ssh and got the following:
```

00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:14.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:14.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:14.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
```

Unfortunately, as you can see, it has exactly tthe same chipset as your card so your card SHOULD use the cx88_dvb driver...

You should be ok though i think Arcsis.

---

### Post by Arcsis on 2007-09-13
I have Tv! Thanks so much for you help Lime, and thanks Jose for a great guide!
:)

---

### Post by elias85 on 2007-09-21
lspci gives:

$ lspci
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
---------------------------------------------------
i tried sudo modprobe cx88_dvb
and got:
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

i tried: sudo modprobe cx88xx and it was ok
i tryied:
tvtime-scanner --input=0
and i got:
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/elias85/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/elias85/.tvtime/stationlist.xml: No existing PAL station list "Custom".
videoinput: Can't get tuner info: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

anyone to help me?

---

### Post by nikoPSK on 2007-09-26
I take it this thread is probably about that card but I don't know where to get drivers for my winfast TV2000 Xp series tv tuner/ recorder.:KS

---

### Post by w4ett on 2007-09-26
A little google always helps:

[http://ubuntuforums.org/showthread.php?p=923127](http://ubuntuforums.org/showthread.php?p=923127)

---

### Post by nikoPSK on 2007-09-28
Thanks, ut I don't get any sound in tvtime.:confused:

---

### Post by w4ett on 2007-09-28
Some users have to run the audio through their  soundcard input jack using a patch cord.

---

### Post by nikoPSK on 2007-09-29
I'm using my onboard audio since my sound blaster audigy (don't know what make) doesn't give sound. I've tried using whatever it's called to adjust / unmute some channels but nothing.:confused:

---

