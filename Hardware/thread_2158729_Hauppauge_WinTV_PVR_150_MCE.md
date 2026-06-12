---
title: "Hauppauge WinTV PVR 150 MCE"
date: 2013-06-30
forum: Hardware
---

### Post by Ash1403 on 2013-06-30
Dear All,
I'm new to Ubuntu, and not very skilled at going 'under the hood'! I'm pretty good at following clear instruction though, so please don't be afraid to treat me like a five year old!

Here's the thing. I've bought myself one of the above and I'm pretty sure I've fitted it correctly (it just slots in, right?),  so I'm assuming that's ok.

Through various pages online, I've installed - I think - the drivers and firmware.

Command:

dmesg | grep ivtv
[FONT=Ubuntu Mono][COLOR=#000000]reveals...

[/COLOR][/FONT][   19.116975] ivtv: Start initialization, version 1.4.3
[   19.117028] ivtv0: Initializing card 0
[   19.117030] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   19.170196] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   19.338953] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   20.068451] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   20.273819] ivtv0: Registered device video1 for encoder MPG (4096 kB)
[   20.273874] ivtv0: Registered device video33 for encoder YUV (2048 kB)
[   20.273936] ivtv0: Registered device vbi1 for encoder VBI (1024 kB)
[   20.273988] ivtv0: Registered device video25 for encoder PCM (320 kB)
[   20.274038] ivtv0: Registered device radio1 for encoder radio
[   20.274040] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   20.274100] ivtv: End initialization
[   20.927513] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   21.128150] ivtv0: Encoder revision: 0x02060039


[FONT=Ubuntu Mono][COLOR=#000000]...from which I'm encouraged to see the card was, at least, autodetected.

TVTime doesn't see a video source. SCANTV doesn't detect any signals either.

Please, what do I do next? 

Here's what I'm using, from System Monitor:
[/COLOR][/FONT]Release 12.04 (precise) 32-bit
Kernel Linux 3.5.0-34-generic
GNOME 3.4.2
Memory: 3.9GiB
[FONT=Ubuntu Mono][COLOR=#000000]Processor: [/COLOR][/FONT]Intel® Core™2 Duo CPU E7400 @ 2.80GHz × 2
Available disk space: 654.2GiB
[FONT=Ubuntu Mono][COLOR=#000000]
What I'm intending to use it for:
I have old VHS (PAL, I'm UK based) tapes which I want to save.
I've connected the VCR to the card using the composite connections.

Many thanks for any help you can offer.

Best wishes
Ash



[/COLOR][/FONT]

---

### Post by gordintoronto on 2013-06-30
What does lspci show?

According to this page: [http://www.mythtv.org/wiki/Hauppauge_PVR-150](http://www.mythtv.org/wiki/Hauppauge_PVR-150)
changing PCI slots sometimes makes a difference. If you have a choice, go close to the CPU.

Do you have a tape playing when you run TVTime?

---

### Post by Ash1403 on 2013-07-01
Hello, and thanks for looking at this with me. Much appreciated.

I don't have a choice of slot, unfortunately.
Yes, I'm playing a tape when running TVTime.

And, whilst I don't understand it, here's the output from lspci...

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G94 [GeForce GT 140] (rev a1)
02:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
02:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

---

### Post by dannyboy79 on 2013-07-01
i'm not familiar with TVTime (and actually tvtime states, "However, tvtime has no MPEG2 decoding capabilities or audio playback code, and therefore cannot be used to watch live TV from these cards.") but according to your dmesg output, your video device node is at /dev/video1. By default though I believe the ivtv driver uses the built in analog tuner as the video source but you're aren't using that, you want to capture the composite connection so you have to use 
```
v4l2-ctl -n
``` to query the various inputs and then use
```
v4l2-ctl -i 2
``` to set the input to the composite input (the number 2 is only an example, use whatever the "-n" returned for composite input)
then it would be as simple as issuing something like this via command line
```
cat /dev/video1 > vhs_tape1.mpg
```
that would take whatever you were playing and capture into a mpg file called vhs_tape1.mpg

I have a pvr-500 and a pvr-350 that I use with mythtv to record tv programs and also a HD-PVR that I capture my xbox 360 with via that same cat command. 

If you really want a GUI to capture what is being captured via the composite connection on the pvr-150 you could look into possibly using VLC
here's a little guide for using VLC: [http://forums.linuxmint.com/viewtopic.php?f=48&t=55754](http://forums.linuxmint.com/viewtopic.php?f=48&t=55754)

---

### Post by Ash1403 on 2013-07-01
Hi, thanks very much for your interest.
Like I say, I'm a newbie at Ubuntu so I'm taking your post, one step at a time.

v4l2-ctl -n gives an output of....

ioctl: VIDIOC_ENUMINPUT
	Input       : 0
	Name        : gspca_pac7302
	Type        : 0x00000002
	Audioset    : 0x00000000
	Tuner       : 0x00000000
	Standard    : 0x0000000000000000 ()
	Status      : 0x00000000 (ok)
	Capabilities: 0x00000000 (not defined)

I'm not interpreting anything I see here as something I can apply to your next step.

Am I missing something?

Thanks very much.

Ash

---

### Post by Ash1403 on 2013-07-30
Bump

---

### Post by gordintoronto on 2013-07-30
Did you try VLC?

---

### Post by kridybel on 2013-08-01
I don't know if it is appropriate direct you to a solution on another forum, but the link below is the one that me finally got me started with my PVR-150:
[http://forums.linuxmint.com/viewtopic.php?f=48&t=55754](http://forums.linuxmint.com/viewtopic.php?f=48&t=55754)

as gordintoronto indicated you should use VLC
```
sudo apt-get install vlc
```

---

