---
title: "soundcard analog output disappeared"
date: 2012-04-19
forum: Hardware
---

### Post by barna on 2012-04-19
Hi,

I have installed kubuntu 11.10 on my girlfriends laptop, and everything worked out of the box, without any tweaking. sound card worked perfectly. I attached an hdmi tv, and while watching it, I closed the lid. The machine was suspended - my fault, I did not change the settings in the power management. When it came up again, it got frozen. At the next boot/login there was an error message in kde saying that the sound card doesnt function properly. Since then I have no sound, only through the hdmi output, so I have to connect the TV if I want to listen to music. In kmix there is only one output channel: Virtual output (I dont know the exact english version, I installed unfortunately in my native language). 

Does anybody have a suggestion what to check, what to reset, etc?

```

cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC270
Codec: Intel IbexPeak HDMI

```

Relevant-looking lines from hwinfo output:
```

 
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0
  E: SUBSYSTEM=sound
  E: SOUND_INITIALIZED=1
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=5 Series/3400 Series Chipset High Definition Audio
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x8086
  E: ID_MODEL_ID=0x3b56
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: SOUND_FORM_FACTOR=internal
  E: PULSE_PROFILE_SET=extra-hdmi.conf

  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  N: snd/hwC0D0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  E: MAJOR=116
  E: MINOR=6
  E: DEVNAME=/dev/snd/hwC0D0
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D3
  N: snd/hwC0D3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D3
  E: MAJOR=116
  E: MINOR=5
  E: DEVNAME=/dev/snd/hwC0D3
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input6
  E: PRODUCT=0/0/0/0
  E: NAME="HDA Intel HDMI/DP,pcm=3"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=100
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw8,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input6/event6
  N: input/event6
  S: input/by-path/pci-0000:00:1b.0-event-sndjack
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input6/event6
  E: MAJOR=13
  E: MINOR=70
  E: DEVNAME=/dev/input/event6
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_SERIAL=noserial
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/input/by-path/pci-0000:00:1b.0-event-sndjack
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
  E: PRODUCT=0/0/0/0
  E: NAME="HDA Intel Mic"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=10
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw4,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input7/event7
  N: input/event7
  S: input/by-path/pci-0000:00:1b.0-event-sndjack
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7/event7
  E: MAJOR=13
  E: MINOR=71
  E: DEVNAME=/dev/input/event7
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_SERIAL=noserial
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/input/by-path/pci-0000:00:1b.0-event-sndjack
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
  E: PRODUCT=0/0/0/0
  E: NAME="HDA Intel Headphone"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=4
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw2,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input8/event8
  N: input/event8
  S: input/by-path/pci-0000:00:1b.0-event-sndjack
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8/event8
  E: MAJOR=13
  E: MINOR=72
  E: DEVNAME=/dev/input/event8
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_SERIAL=noserial
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/input/by-path/pci-0000:00:1b.0-event-sndjack
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  N: snd/pcmC0D0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  E: MAJOR=116
  E: MINOR=4
  E: DEVNAME=/dev/snd/pcmC0D0c
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  N: snd/pcmC0D0p
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  E: MAJOR=116
  E: MINOR=3
  E: DEVNAME=/dev/snd/pcmC0D0p
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D3p
  N: snd/pcmC0D3p
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D3p
  E: MAJOR=116
  E: MINOR=2
  E: DEVNAME=/dev/snd/pcmC0D3p
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  N: snd/controlC0
  S: snd/by-path/pci-0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  E: MAJOR=116
  E: MINOR=7
  E: DEVNAME=/dev/snd/controlC0
  E: SUBSYSTEM=sound
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/snd/by-path/pci-0000:00:1b.0
  E: TAGS=:udev-acl:
  

```

```

lsmod | grep snd
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  1 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm

lsmod | grep rt (for realtek???)
parport_pc             32114  0 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              393421  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172427  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
parport                40930  3 parport_pc,ppdev,lp

```

lspci output
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

/etc/modprobe.d/alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

```
Thank you

---

### Post by samigina on 2012-04-19
Pulseaudio and Kmix have some problems working together, disappeared soundcards is a know problem.

Try removing the ./pulse directory and reboot.

---

### Post by SeijiSensei on 2012-04-19
Also check System Settings > Multimedia > Phonon and make sure KDE is using the correct audio channels.  You might try setting the video audio output to the HDMI connector and the music output to the internal audio device.

---

### Post by barna on 2012-04-19
This was it, thanks a lot. Great!

> **samigina said:**
> Pulseaudio and Kmix have some problems working together, disappeared soundcards is a know problem.

Try removing the ./pulse directory and reboot.

---

### Post by samigina on 2012-04-19
Nice.

Dont forget to mark the post "solved"

---

