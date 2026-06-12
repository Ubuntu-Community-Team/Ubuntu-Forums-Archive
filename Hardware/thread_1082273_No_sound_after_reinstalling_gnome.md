---
title: "No sound after reinstalling gnome"
date: 2009-02-27
forum: Hardware
---

### Post by anjpr on 2009-02-27
I installed KDE in my laptop.  I did a complete removal of gnome except for the files associated with firefox and evolution.  Everything was working ok in KDE but I preferred to go back to gnome.  Missed the gnome applications which I'm familiar with.  Upon reinstalling, gnome there's no sound.  I did a complete removal of KDE.

I ran the following script in terminal:

cat /proc/asound/cards
grep ^Codec /proc/asound/card?/codec*
lsmod | grep snd
lspci   (just the bit for the soundcard)

and this is what I got:

[B][SIZE="5"]
cat /proc/asound/cards[/SIZE][/B]
HDA-Intel - HDA ATI 
HDA ATI SB at 0xd6400000 irq 16

[B]
[SIZE="5"]grep ^Codec /proc/asound/card?/codec*[/SIZE][/B]
/proc/asound/card0/codec#0:Codec: Realtek ALC268
/proc/asound/card0/codec#1:Codec: LSI ID 1040

[SIZE="5"]**lsmod | grep snd**[/SIZE]
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm

[SIZE="5"]**lspci**[/SIZE]
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

Can anyone help!

---

### Post by kestrel1 on 2009-02-27
Can you post the results from the following two files: options & alsa-base
To do this type these commands in the terminal:```
gedit /etc/modprobe.d/alsa-base
```
&```
gedit /etc/modprobe.d/options
```

---

### Post by anjpr on 2009-02-27
**[SIZE="5"]gedit /etc/modprobe.d/alsa-base:[/SIZE]**

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
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
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

**[SIZE="5"]gedit /etc/modprobe.d/options[/SIZE]**

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1

---

### Post by kestrel1 on 2009-03-02
Add the following to your alsa-base & options files> options snd-hda-intel model=mobile
Make a backup first ```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
```
```
sudo cp /etc/modprobe.d/options /etc/modprobe.d/options.bak
```
Then edit the files:```
sudo gedit /etc/modprobe.d/alsa-base
```
```
sudo gedit /etc/modprobe.d/options
```
Just add the options line at the end of each file & save them.
Reboot & hopefully you will be good to go.

---

