---
title: "Audio problems on laptop ASUS F3Ja - ICH7 Family sound card"
date: 2008-07-01
forum: Hardware
---

### Post by manolomanolo on 2008-07-01
Hi to all.

**lspci -nn | grep -i audio**
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)

I have some problems with that soundcard.

1) **When booting** I get the following error:
> kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory

2) **Cannot change volume** using Fn + F11 and Fn + F12 keys; cannot mute using the Fn + F10 key. When I press them I can see an icon as muting/unmuting audio and moving a slidebar as varying volume but actually audio still plays  the same way: actually it doesn't mute/unmute nor changes volume. I can do change volume using the Volume Control applet or alsamixer.

3) **Ekiga** gives the following error when testing sound using Configuration Druid:
> Failed to open the device

Impossible to open the selected audio device (HDA Intel) for playing. Please check your audio setup, the permissions and that the device is not busy.
In this case I0ve tried to kill -9 pulseaudio and redo the audio test but nothing changed.

I've been trying to modify /etc/modprobe.d/alsa-base adding and un-commenting respectively those last lines in **bold character** but I still have those problems.

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
[B]#options snd-hda-intel model=asus
#options snd-hda-intel model=z71v position_fix=1
options snd-hda-intel model=asus-laptop[/B]

---

### Post by dogscoff on 2008-07-01
Can't help on points 1 and 3, but I have had fun and games with laptop Fn keys before. Do you know if FN keys are supported out of the box by your distro on this laptop? Do any of the other FN combos work? If it isn't (or you don't know) then it might be that you have to fiddle about with keymappings to get it working.

For example, to get the volume FN shortcuts working on my old Sony, I had to add the following lines to the file .Xmodmap:

keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute

This was under Xubuntu, Feisty. IIRC there was some software you could run that would show the keycodes produced by each keystroke, enabling you to capture the codes you need and assign functions to them.

I very much doubt that the keycodes above will be the right ones for your hardware, but maybe it will be enough to start you down a productive path of googling..? 

Good luck!

---

### Post by manolomanolo on 2008-08-21
Any other alternative?
Thanks.

---

