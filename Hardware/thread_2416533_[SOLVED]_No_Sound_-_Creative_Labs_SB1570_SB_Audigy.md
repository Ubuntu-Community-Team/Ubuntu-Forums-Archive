---
title: "[SOLVED] No Sound - Creative Labs SB1570 SB Audigy Fx - Ubuntu 18.04"
date: 2019-04-11
forum: Hardware
---

### Post by draxbear on 2019-04-11
A few threads on this one but none with a clear conclusion or summary sadly. I've just installed the card but don't have any sound output on the green rear "front/headphones" connector with any analogue device option. It is at least detecting the card ok!

Some info requested by the other threads to get things rolling.

Hopefully someone can help me with the right syntax for the alsa-base.conf file to get things going.


```

sudo lspci -v

04:00.0 Audio device: Creative Labs Sound Core3D [Sound Blaster Recon3D / Z-Series] (rev 01)
        Subsystem: Creative Labs SB1570 SB Audigy Fx
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fe104000 (64-bit, non-prefetchable) [size=16K]
        Memory at fe100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
        Capabilities: [70] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [170] Device Serial Number 00-00-00-00-00-00-00-00
        Capabilities: [180] Power Budgeting <?>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel

```

```

cat /etc/modprobe.d/alsa-base.conf

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

Output from [alsa-project diagnostic script]("https://wiki.ubuntu.com/Audio/AlsaInfo") - [http://alsa-project.org/db/?f=a6602b43d53b8212b05b7427ff0ee3d85d8ca485]("here"):p

---

### Post by shspvr on 2019-04-20
Have check in Alsamixer maybe the HP/Speaker need to be enabled if use m key to enable it

---

### Post by kryten35 on 2019-04-21
Have the same card.The headphone out has never worked on linux for me,ive been trying for about 4 years.The fault is creative not sharing info with linux.Also missed having the system wide graphic equaliser software which works in windows.

Switched to sound output  via HDMI  to screen and used the screens headphone output.
Installed PULSE EFFECTS  and used the equaliser in that instead.Sound quality is just as good once you adjust it.

---

### Post by draxbear on 2019-04-22
Thanks for chipping in Shspvr. I had a go changing the volume in alsamixer from a terminal session as myself and it appears to have done the trick somehow. I rebooted to make sure it stuck across a restart and look like I'm ok to go from here now!

Just for reference (and hopefully kryten35):

I've plugged the speakers into the "green" output port on the creative card with a standard headphone style jack and it seems to be doing ok. In the Sound settings GUI, moving the "Line Out - Sound Core3D [Sound Blaster Recon3D / Z-Series] (SB1570 SB Audigy Fx)" output volume makes the "Master" volume bar on the Alsamixer v1.1.3 "Card: HDA Creative, Chip: Realtek ALC898, Item: Master". The profile in the Sound GUI is "Analogue Stereo Output".

---

