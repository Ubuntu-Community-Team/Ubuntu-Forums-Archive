---
title: "What is wrong???why this???help please, please friends..."
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by AFCB on 2008-02-19
hello masters...

i'm a nem ubuntu user..nad i'm loving what im seing..

but there are a problem...

i have instaled the OS... upgraded the video driver.. everything work fine...but... where is the sound?????????????????....

with the aplay -l comand i have this:
[I]
placa 0: Intel [HDA Intel], dispositivo 0: CMI9880 [CMI9880]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0[/I]

so... i have searched over the web and i have finded that i have to edit the alsa-base file and ond out at the end the line.* options snd-hda-intel model=minimal*

my file is now:

[I]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
**options snd-hda-intel model=minimal**[/I]

but i don't have sound.. only my headphones works...

i want to stay with ubuntu.. a say biy to windows.. but with no sound i can do that..

please friends i believe only on you:(:(:(

waiting my friends:confused::confused::confused:

regards
thanks for your time7

sorry for the english...i'm portuguese..

---

