---
title: "Help configuring Acer Aspire 8942G"
date: 2010-05-14
forum: Hardware
---

### Post by fballem on 2010-05-14
I have just done a fresh install of Ubuntu 10.04 on an Acer Aspire 8942G laptop. I have used ubuntu for a couple of years on my desktop, and I have been really happy with it.

I have two issues with the installation on this laptop:

[LIST=1]
[*]The laptop has an ATI Mobility Radeon HD 5650 which provides the video. The ATI driver does not support it, which is fine, since I do not use Desktop effects.
[*]The computer has a built-in CineSurround 5:1 system with 6 speakers. This is a much larger issue, since the sound comes out of only one speaker.
[/LIST]

I would like some help to see if the sound can be made to work.

I do have the ubuntu-audio-dev ppa enabled, but no idea what I need to do to get the sound working.

I can do very basic terminal commands, if you give me very specific instructions. I don't want to drown you in useless information, so if we could start with commands that will tell you more of what is in my machine, then I will be happy to run those and post them on this thread.

Assuming that we can make this work, then I will document the required steps here.

Thanks in advance, and really looking forward to getting sound working properly.

---

### Post by fballem on 2010-05-17
output from lspci:

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

any help would be much appreciated.
Thanks,

---

### Post by fballem on 2010-05-17
output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Looks like my first problem is that ubuntu is not picking up the Intel card, but I could be wrong. If someone could please tell me how to fix that, then it might go a long way to starting to fix the problem.

Thanks,

---

### Post by lidex on 2010-05-17
Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

---

### Post by fballem on 2010-05-18
As requested,

output from uname -a:

```

Linux ballemco-06 2.6.32-22-server #33-Ubuntu SMP Wed Apr 28 14:34:48 UTC 2010 x86_64 GNU/Linux

```

output from cat /proc/asound/version;

```

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-server (SMP).

```

output from head -n 1 /proc/asound/card*/codec#*:

```

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 670

==> /proc/asound/card3/codec#0 <==
Codec: ATI R6xx HDMI

```

By the way, if it helps, when I had Windows 7 installed on this machine, it was using a Realtek 889 codec and the sound worked fine.

I hope that this suggests a solution to you.

Many thanks,

---

### Post by lidex on 2010-05-18
I would start with an alsa upgrade via the alsa-upgrade link in my sig. Have you added any options to alsa-base.conf?

---

### Post by fballem on 2010-05-18
The script does not appear to have worked correctly. After carefully running all of the steps, I have no sound and no devices in the sound preferences. Some output that may be helpful:

cat /proc/asound/version
```

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-server (SMP).

```

head -n 1 /proc/asound/card*/codec#*
```

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 670

==> /proc/asound/card3/codec#0 <==
Codec: ATI R6xx HDMI

```

aplay -l
```

aplay: device_list:235: no soundcards found...

```

I am patient - and certainly not panicked, since I have very good backups, so if you would like to continue with this, then I would as well.

Any further suggestions would be much appreciated

I am also providing my alsa-base.conf file, which should answer your question about options. Please note that as far as I can tell, this file is not changed from before I ran your script.

alsa-base.conf
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

```

---

### Post by lidex on 2010-05-18
OK. Try this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
Reboot.

---

### Post by fballem on 2010-05-19
I have some sound back. It comes out of one speaker, same as I had when I started this.

By the way, there are two other things that I should mention:

1. I have enabled ppa:ubuntu-audio-dev/ppa in my sources.
2. I have logitech chat pro headphones plugged into a USB port. These are stereo headphones with a boom mic. If I change the output in pulse audio to the headphones, they do work as expected (sound out of both sides, mic works). 

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L
```

pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
front:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Generic
    HD-Audio Generic, ATI HDMI
    HDMI Audio Output

```

cat /proc/asound/version
```

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-server (SMP).

```

head -n 1 /proc/asound/card*/codec#*
```

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 670

==> /proc/asound/card3/codec#0 <==
Codec: ATI R6xx HDMI

```

Nothing is changed in my alsa-base.conf and I have no options selected.

---

### Post by fballem on 2011-03-27
I was reminded of this thread while I was reviewing my subscribed threads. I have done a clean install of ubuntu 10.10 on the Acer Aspire 8942G and it is working very cleanly - no issues, no need to enable different ppa repositories. I will mark this as solved.

---

