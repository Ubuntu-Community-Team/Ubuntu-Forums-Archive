---
title: "nvidia 430 video/sound problems"
date: 2015-02-02
forum: Hardware
---

### Post by linuxn00b1 on 2015-02-02
I have a fresh install of xubuntu 14.04 32bit on a pc that previously ran xbmcbuntu frodo with no problem video and DTS audio worked perfectly. This pc is hooked up to a denon avr and 50inch samsung 1080p tv.

I had no sound and the desktop was way too big for the tv (cut off around corners) with preinstalled generic video driver. I did some googling and found a way to get nvidia drivers for xubuntu 14 still the same problem. I set the underscan in nvidia properties (right click on desktop) and no matter how small I make the picture on the tv the right half of a browser window is cutoff and so is the right half of the desktop  (clock and calander ) The resolution is set to 1080p. also I have no sound over hdmi. I clicked the sound profile near the clock and set to hdmi and enabled ac3 and DTS and still nothing. 

sudo lshw -C display 

*-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 430]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fb000000-fbffffff memory:c8000000-cfffffff memory:d6000000-d7ffffff ioport:df00(size=128) memory:d0000000-d007ffff

lspci 

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)


I swear I ran a command that showed hdmi set to on for audio but 

~$ aplay -l
aplay: device_list:268: no soundcards found...

I'm lost. Utimately I would like this to be a media center using xbmc/kodi so once I get the picture set and sound working optimal setting tips would be great. 


thanks in advance

---

### Post by linuxn00b1 on 2015-02-03
so turns out aplay -l wasn't returning any information because the desktop went to lock screen. when login screen is up I get zero output from aplay -l, when desktop user is logged in locally I get a response. I have been running terminal via ssh over wifi. why is that ? 
so aplay -l now shows:
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

running speaker-test -D hw:1,9 -c 6 (changing out the 9 with all the hdmi devices) 

Playback device is hw:1,9
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib pcm_hw.c:1667:(_snd_pcm_hw_open) Invalid value for card
Playback open error: -2,No such file or directory

also using alsamixer all spdif listing are 00 (although when I first run alsamixer it shows onboard audio first, but when I hit f6 I see the nvidia card)
I just found out I can't run alsamixer (over ssh) when the desktop lockscreen is up either.

---

### Post by efflandt on 2015-02-08
It has been awhile since I had a GT 430 (it was a cheap Galaxy card that failed after 1 yr warranty ran out). Since Ubuntu 12.04 I think, the system should automatically be able to use the correct HDA Nvidia device for HDMI audio assuming that you have system sound set to "HDMI/DisplayPort,HDA Nvidia", unless something is muted. Assuming you installed nvidia drivers from Ubuntu packages, and not with a script from nvidia, what shows for```
dpkg-query -l nvidia*
```

This is what alsamixer shows for defaults when I have that selected with my current Nvidia card```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.27.2 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel MID                                  F1:  Help               &#9474;
&#9474; Chip: Intel IbexPeak HDMI                            F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -12.00]                       Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9474;
&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;OO&#9474;     &#9474;MM&#9474;              &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;      56    100<>100 100<>100 100<>100   0<>0    22<>22  100<>100   100       &#9474;
&#9474;  < Master >Headphon   PCM     Front   Front Mi Front Mi Surround  Center     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```Although, that may be for main audio and if you press F6 and select HDA NVidia, the S/PDIF devices (no volume controls there) all should show 00 (on) and not MM (mute).

Are you using straight HDMI or DVI to HDMI? HDMI audio works for me even using DVI to HDMI cable (GTX 200-series or newer should support that [http://en.wikipedia.org/wiki/Digital_Visual_Interface#DVI_and_HDMI_compatibility](http://en.wikipedia.org/wiki/Digital_Visual_Interface#DVI_and_HDMI_compatibility) ). Note that if I set my HDTV to 16:9 it does overscan, but set to "Just Scan" (on LG or maybe Full Screen on others) the 1080p display is properly sized/centered.

Not sure how to control (or port?) audio through ssh, but for something like XBMC you might consider a wireless keyboard/mousepad and/or mouse instead.

---

### Post by linuxn00b1 on 2015-02-08
I installed the drivers from a thrid party repo b/c I read somewhere nvidia didn't support 14.04 and the generic drivers were giving me the same issues i'm trying to fix.

dpkg-query -l nvidia* gives me:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nvidia-304     304.125-0ubu i386         NVIDIA legacy binary driver - ver
un  nvidia-common  <none>       <none>       (no description available)
ii  nvidia-current 304.125-0ubu i386         Transitional package for nvidia-c
un  nvidia-driver- <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-opencl- <none>       <none>       (no description available)
ii  nvidia-opencl- 304.125-0ubu i386         NVIDIA OpenCL ICD
un  nvidia-prime   <none>       <none>       (no description available)
ii  nvidia-setting 346.35-0ubun i386         Tool for configuring the NVIDIA g
un  nvidia-setting <none>       <none>       (no description available)
un  nvidia-vdpau-d <none>       <none>       (no description available)

as far as ssh goes i'm just using it to send commands since the picture is not fit to the TV screen properly it's easier to see on my laptop
I tried running alsamixer, but I can't. For some reason if the desktop has a login screen or the display goes to sleep any nvidia/sound command won't work.
But I do know the screen that looked like that, there was nothing muted.

---

