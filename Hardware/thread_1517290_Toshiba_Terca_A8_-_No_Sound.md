---
title: "Toshiba Terca A8 - No Sound"
date: 2010-06-24
forum: Hardware
---

### Post by 2edgesword on 2010-06-24
Everything else seems to be working fine (video, wi-fi, etc.) but I have no sound. I've verified using Alsamixer that audio is not muted and tried some of the fixes I found on-line but none worked.

Thanks in advance for any help you can provide.

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by 2edgesword on 2010-06-25
I've been doing a lot of searching around. One comment was regarding a conflict in that the modem driver was being applied as the audio driver. Is this possible and is there a way to check that the correct audio driver is being used to run the audio?

---

### Post by lidex on 2010-06-25
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

This as well:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by 2edgesword on 2010-06-25
[B]The outputs are as follows:

uname -a

[/B]Linux paul-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
[B]
aplay -l

[/B]**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[B]

dpkg -l | grep "alsa"

[/B]ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-22-generic 2.6.32-22.13                                    Ubuntu supplied Linux modules for version 2.[B]

head -n 1 /proc/asound/card*/codec#*

[/B]==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC262

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054

---

### Post by lidex on 2010-06-25
I note you have alsa-backports installed. Was this in response to audio issue or did you install before? Was this an upgrade or clean install of lucid? What about the output of that last command? Hmmm....that doesn't sound bossy at all ;)

---

### Post by 2edgesword on 2010-06-25
```
 USER        PID ACCESS COMMAND
/dev/snd/controlC0:  paul       1280 F.... pulseaudio
                     paul       1452 F.... alsamixer

```

The laptop is a Toshiba Tecra A8-EZ8311

---

### Post by 2edgesword on 2010-06-25
> **lidex said:**
> I note you have alsa-backports installed. Was this in response to audio issue or did you install before? Was this an upgrade or clean install of lucid? What about the output of that last command? Hmmm....that doesn't sound bossy at all ;)

It was a clean install of Ubuntu 10.04 and I don't have a clue aobut the alsa-backports.

---

### Post by lidex on 2010-06-25
It's not the modem driver. Let's try this.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=toshiba 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by 2edgesword on 2010-06-25
Done...

On sound preference it says

Hardward is "Internal Audio, 1 output/ 1 input Analog Stero Duplex" 

Input is "Internal Audio Analog Stereo"

Output is "Internal Audio Analog Stereo"

Applications is "No application is currently playing or recording"

I'll reboot and see what happens. Thanks for your help.

---

### Post by 2edgesword on 2010-06-25
After reboot no sound.

BTW, the slides on alsamixer are labelled "Master" "PCM" "Front Mic" "Front Mic Boost" "Mic" "Mic Boost" "Beep" "Caller I" "Off Hook"...

There no slides labelled speakers. Is this the normal labelling for the slides?

---

### Post by lidex on 2010-06-25
Yes. Generally master and/or pcm control volume. 
Use this line instead in alsa-base.conf:
```
options snd-hda-intel enable=1 index=0 model=basic
```
Make sure to delete the first one and reboot to affect changes.

---

### Post by 2edgesword on 2010-06-26
I made the change and the conf file reads....

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel enable=1 index=0 model=basic
```

But still no sound :(

---

### Post by 2edgesword on 2010-06-26
Hi lidex

Although I still don't have sound I appreciate your suggestions at  trying to fix the issue. Apparently I'm not alone with respect to this  model of Toshiba laptop and it appears that the fix for some doesn't  work for others.

If you have any other suggestions let me know. I'm loving the new found  speed and utility of the machine, and if I can get the sound working  would be the icing on the cake.

---

### Post by lidex on 2010-06-26
I saw one user had success with this option:
```
options snd-hda-intel model=hippo
```

Full list:
```
ALC262
======
  fujitsu	         Fujitsu Laptop
  hp-bpc	         HP xw4400/6400/8400/9400 laptops
  hp-bpc-d7000   HP BPC D7000
  hp-tc-t5735	 HP Thin Client T5735
  hp-rp5700	HP RP5700
  benq		Benq ED8
  benq-t31	Benq T31
  hippo		Hippo (ATI) with jack detection, Sony UX-90s
  hippo_1	         Hippo (Benq) with jack detection
  sony-assamd	   Sony ASSAMD
  toshiba-s06	 Toshiba S06
  toshiba-rx1	 Toshiba RX1
  tyan		 Tyan Thunder n6650W (S2915-E)
  ultra		 Samsung Q1 Ultra Vista model
  lenovo-3000	  Lenovo 3000 y410
  nec		         NEC Versa S9100
  basic		 fixed pin assignment w/o SPDIF
  auto		 auto-config reading BIOS (default)
```

---

### Post by 2edgesword on 2010-06-26
lidex

There are a few on the list I haven't tried so I'll plug them in and see what happens.

Thanks

---

### Post by 2edgesword on 2010-06-26
No joy on the other options. The sound was working under Windows last week so I don't think it's a hardware failure but you never know.

If anyone has any other suggests let me know. Thanks for the help so far.

---

### Post by 2edgesword on 2010-06-28
Hi Folks,

I found the solution to the issue here: 

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/115966](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/115966)

It was a matter of reinstalling Windows and manually turning on the speakers using the function buttons (in my case with the Toshiba that means holding the Fn key and clicking the Esc key) and then reloading Ubuntu. I did not have to change the alsa-base.conf file as referenced in the instructions.

Thanks for the attempts to solve my problem. It's amazing to me that some of the solutions suggested did in fact solve the problem for others using the Toshiba Terca but not with my particular machine.

Paul

---

### Post by UBM7Tablet on 2010-07-02
I can confirm the Toshiba laptop sound settings behavior.

I have a Toshiba Tecra M7, dual boot with Windows and UB 10.04.

I find that if I shutdown Windows with the sound control/speakers in the muted state, when I next boot into Ubuntu, no sound will play from speakers or headphones, regardless of the Ubuntu Mute/Unmute state or volume setting.

A reboot into Windows, setting UnMute via the volume control then reboot to Ubuntu makes sound available again.

Tosh must be storing the windows speaker state in BIOS(?).  

This laptop also does auto-sensing to mute speakers when headphone jack is in use; this may have a similar effect on UB.

---

