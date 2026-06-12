---
title: "Sound problem, dv7-3199eo"
date: 2010-07-25
forum: Hardware
---

### Post by Hogberg on 2010-07-25
Ubuntu 10.04 
HP Dv7-3199eo

Have sound out to the main speakers. 
Have sound in working with skype 
3.5 works but need alsa mixer to get sound. Can't listen to 3.5 and have no sound on main speakers. 
3.5 input don't work
xb3000 can't get sound
[http://www.google.com/images?client=ubuntu&channel=fs&q=xb3000&oe=utf-8&um=1&ie=UTF-8&source=univ&ei=tAVMTMqDMoqTOJ2uwZYD&sa=X&oi=image_result_group&ct=title&resnum=4&ved=0CD8QsAQwAw&biw=1600&bih=675](http://www.google.com/images?client=ubuntu&channel=fs&q=xb3000&oe=utf-8&um=1&ie=UTF-8&source=univ&ei=tAVMTMqDMoqTOJ2uwZYD&sa=X&oi=image_result_group&ct=title&resnum=4&ved=0CD8QsAQwAw&biw=1600&bih=675)
(Put in something to 3.5 don't break the other sound)

*************
With 9.10 the computer sounded like old old old recordplayer. That fixed with 
/etc/modprobe.d/alsa-base.conf

delete
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

and put in 
options snd-hda-intel model=dell-m4-2[FONT=monospace]
[/FONT]options snd-hda-intel enable_msi=1[FONT=monospace]
[/FONT]options snd-hda-intel model=hp-dv5

That fixed some sound. The main speakers and build in mic but not xb3000 and put in any headset etc. 
***********************

Put in "options snd-hda-intel enable_msi=1" to alsa-base.conf helps not.
***********************
lspci I found 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)


jonas@dv7:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 230M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

*******************
Have Gnome alsa-mixer 
Have 2 "view"
IDT 92HD75B3X5 : a lot of things 
Nvidia ID a : noting under it 

Master speaker PCM Front move strange when I +- and make things wrong. 
*******************
gstreamer-properties
found some info in the week but never seen this before. Have traid some but never got sound out to xb3000.

jonas@dv7:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

*******************

jonas@dv7:~$ lshw -c multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:d3000000-d3003fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:db100000-db103fff
********************
Getting  sick tired not having this good laptop work as it should. Have had a  lot of multi **** with sound, grafik, grub, sync... But have not manage  to fix the sound. Feel most of the time I spend time to get this good  computer to work with ubuntu and it only getting old and not having  pleaser to use it when it still new.

---

### Post by Hogberg on 2010-07-25
Have this info to

jonas@dv7:~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: STAC92xx Analog [STAC92xx Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 1: STAC92xx Digital [STAC92xx Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

---

### Post by lidex on 2010-07-25
Can you post the output of these terminal commands for me please:
```
uname -a
dpkg -l | grep "alsa"

```
Terminal="Applications->Accessories->Terminal"

---

### Post by Hogberg on 2010-07-25
jonas@dv7:~$ uname -a
Linux dv7 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
jonas@dv7:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsnack2-alsa                        2.2.10-dfsg1-9                                  Sound extension to Tcl/Tk and Python/Tkinter

---

### Post by Hogberg on 2010-07-25
Right now I like ubuntuforums.org :D 
find some more terminal code to get info about the sound. Post some from terminal. Strange that I have two 0 <==


jonas@dv7:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID a

---

### Post by lidex on 2010-07-25
I usually ask for that but I have the same laptop with the same codec. The other codec is for hdmi, which is through the video card - card 1. The onboard audio is card 0. You have codec 0 on card 0 and codec 0 on card 1.

---

