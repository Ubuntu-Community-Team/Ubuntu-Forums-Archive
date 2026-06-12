---
title: "pc-speaker no sound..."
date: 2013-02-11
forum: Hardware
---

### Post by ringtail2013 on 2013-02-11
Hi!

I want to clarify that I have sound in external speakers[btw do not use them], but I need the pc-speaker

got Buntus 12.10 and Xp(on Xp sound works fine-without external speakers-)

```
 $ lsmod | grep snd
snd_intel8x0           33107  2 
snd_ac97_codec        105652  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                80235  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_intel8x0,snd_pcm

```

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

```
 This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```
alsamixer:
[http://ompldr.org/vaGZtaQ/Screenshot%20from%202013-02-11%2012:27:43.png](http://ompldr.org/vaGZtaQ/Screenshot%20from%202013-02-11%2012:27:43.png)

ask 4 more outputs...

tia!

---

### Post by ringtail2013 on 2013-02-12
no one?

---

### Post by Yellow Pasque on 2013-02-12
And what happens when you try to load the module?:
```
sudo modprobe -v pcspkr
```

If that starts making it work, then you probably should find the sections that says:
```
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

```
..and put a '#' in front of the blacklist lines.

---

### Post by ringtail2013 on 2013-02-12
> **Temüjin said:**
> And what happens when you try to load the module?:
```
sudo modprobe -v pcspkr
```

```
 # modprobe -v pcspkr
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/input/misc/pcspkr.ko 

```
'nada'!

---

### Post by Yellow Pasque on 2013-02-12
Hmmm, I;m not sure what the difference is between pcspkr and snd-pcsp. Maybe this would work (if not, I'm out of ideas):
```
sudo modprobe -v pcspkr snd-pcsp
```

---

### Post by ringtail2013 on 2013-02-12
thx man!

sudo modprobe -v pcspkr snd-pcsp

```
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/input/misc/pcspkr.ko snd-pcsp
FATAL: Error inserting pcspkr (/lib/modules/3.5.0-23-generic/kernel/drivers/input/misc/pcspkr.ko): Invalid argument
```

---

### Post by Yellow Pasque on 2013-02-13
Sorry, I screwed up the syntax on that last one:
```
sudo modprobe -v pcspkr
sudo modprobe -v snd-pcsp
```

---

### Post by ringtail2013 on 2013-02-13
```
 sudo modprobe -v snd-pcsp
insmod /lib/modules/3.5.0-23-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko index=-2
FATAL: Error inserting snd_pcsp (/lib/modules/3.5.0-23-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko): Device or resource busy
```

Why does it have to be so hard?

---

### Post by ringtail2013 on 2013-02-13
up!

probably changing distro fix the inconvenient...

---

### Post by ringtail2013 on 2013-02-14
=d>

---

