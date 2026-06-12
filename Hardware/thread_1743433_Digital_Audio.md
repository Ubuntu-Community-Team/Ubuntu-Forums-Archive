---
title: "Digital Audio"
date: 2011-04-29
forum: Hardware
---

### Post by mdhollis on 2011-04-29
I have not been able to use my digital audio output since lucid.  It worked in karmic but since then I only have analog audio.  I have tried numerous things and I was wondering if anyone had any insight.

```
18: PCI 05.0: 0403 Audio device
  [Created at pci.318]
  Unique ID: CvwD.IMQ+L+rzeU7
  SysFS ID: /devices/pci0000:00/0000:00:05.0
  SysFS BusID: 0000:00:05.0
  Hardware Class: sound
  Model: "nVidia MCP61 High Definition Audio"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03f0 "MCP61 High Definition Audio"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a66 
  Revision: 0xa2
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe028000-0xfe02bfff (rw,non-prefetchable)
  IRQ: 22 (298 events)
  Module Alias: "pci:v000010DEd000003F0sv0000103Csd00002A66bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by lidex on 2011-04-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

Reference:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

---

### Post by mdhollis on 2011-05-01
Thanks for the reply.  I'm using a SPDIF output. In sound preferences -> hardware it only shows a analog device.

[http://www.alsa-project.org/db/?f=3bb1fcad7da8c0fd80359df09deab7e442df57da]("http://www.alsa-project.org/db/?f=3bb1fcad7da8c0fd80359df09deab7e442df57da")

---

### Post by mdhollis on 2011-05-01
Just some more info...

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```


```
 cat /proc/asound/devices
  1:        : sequencer
  2: [ 0- 2]: digital audio capture
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0- 0]: hardware dependent
  6: [ 0]   : control
 33:        : timer

```

---

### Post by lidex on 2011-05-01
Open this file:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add this text at the bottom:
```
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1
```
Save. Close. Reboot.

---

### Post by mdhollis on 2011-05-01
OK so I edited /etc/modprobe.d/alsa-base.conf, then rebooted with no success.  

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
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1

```

:confused:

---

### Post by lidex on 2011-05-01
Check aplay -l now. Here's what it was:
```
APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Alsa is not recognizing your digital device. I'm seeing issues in natty now that are some kind of regression for that codec. Seems to manifest differently in different configurations so I have not been able to figure out a fix. I definitely think the devs need to be involved here. File a bug using this method ```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by mdhollis on 2011-05-01
Again thanks for the help.  I filed a bug about this a couple of days ago.  I'm always uneasy about filing a bug so I wanted to be certain. 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Still only recognizing my analog device.  I'll be sure to post an solution if I get one. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/773572]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/773572")

---

### Post by lidex on 2011-05-02
> **mdhollis said:**
> Again thanks for the help.  I filed a bug about this a couple of days ago.  I'm always uneasy about filing a bug so I wanted to be certain. 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Still only recognizing my analog device.  I'll be sure to post an solution if I get one. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/773572]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/773572")

Thank you for your persistence. I am currently trying to subscribe to your bug as I would like to see a fix for this. Launchpad seems slow, at least.

---

