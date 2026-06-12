---
title: "My soundcard on studio 1749 ubuntu 10.10 does not work"
date: 2011-06-26
forum: Hardware
---

### Post by dennis605 on 2011-06-26
hi lovely community,

could please someone help me to get my soundcard working?
I try to post all relevant informations you maybe need.
```
dennis@dennis-Studio-1749:~$ lsb_release -d
Description:	Ubuntu 10.10
dennis@dennis-Studio-1749:~$ uname -r
2.6.35-25-generic
dennis@dennis-Studio-1749:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0300000 irq 47
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xcfedc000 irq 48
dennis@dennis-Studio-1749:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: STAC92xx Analog [STAC92xx Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 1: Generic [HD-Audio Generic], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
dennis@dennis-Studio-1749:~$ aplay /usr/share/sounds/alsa/Noise.wav
Wiedergabe: WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono
dennis@dennis-Studio-1749:~$ lspci -nnk | grep -iA2 audio 
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
	Subsystem: Dell Device [1028:041b]
	Kernel driver in use: HDA Intel
--
02:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
	Subsystem: Dell Device [1028:041b]
	Kernel driver in use: HDA Intel
dennis@dennis-Studio-1749:~$ ps -C esd
  PID TTY          TIME CMD
dennis@dennis-Studio-1749:~$ ps -C arts
  PID TTY          TIME CMD
dennis@dennis-Studio-1749:~$ ps -C pulseaudio
  PID TTY          TIME CMD
 2267 ?        00:00:04 pulseaudio
dennis@dennis-Studio-1749:~$ grep "^audio" /etc/group | grep "$USER" | wc -l
1
dennis@dennis-Studio-1749:~$ lsmod | grep "snd"
snd_hda_codec_hdmi     26909  1 
snd_hda_codec_idt      69222  1 
snd_hda_intel          27627  3 
snd_hda_codec         100236  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6674  1 snd_hda_codec
snd_pcm                95653  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi            6412  0 
snd_rawmidi            22710  1 snd_seq_midi
snd_seq_midi_event      7195  1 snd_seq_midi
snd_seq                61487  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23976  2 snd_pcm,snd_seq
snd_seq_device          7034  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    70823  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8780  2 snd_hda_intel,snd_pcm
dennis@dennis-Studio-1749:~$ head -n 3 /proc/asound/card0/codec#0
Codec: IDT 92HD73C1X5
Address: 0
AFG Function Id: 0x1 (unsol 1)
dennis@dennis-Studio-1749:~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head: „/proc/asound/card0/codec97#0/ac97#0-0“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden
dennis@dennis-Studio-1749:~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs
head: „/proc/asound/card0/codec97#0/ac97#0-0+regs“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden
dennis@dennis-Studio-1749:~$ asoundconf list
asoundconf: Befehl nicht gefunden
dennis@dennis-Studio-1749:~$ cat ~/.asoundrc
cat: /home/dennis/.asoundrc: Datei oder Verzeichnis nicht gefunden
dennis@dennis-Studio-1749:~$ cat ~/.asoundrc.asoundconf
cat: /home/dennis/.asoundrc.asoundconf: Datei oder Verzeichnis nicht gefunden
dennis@dennis-Studio-1749:~$ 
alsa-base.conf:

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
options snd-hda-intel modell=dell
options snd-hda-intel index=0

```

Please help me i'm getting cracy with this.
Thanx for your help.
dennis605

---

### Post by wolfen69 on 2011-06-26
Did you check all the sound settings? Intel sound should work.

---

### Post by dennis605 on 2011-06-26
Hi wolfen69,

thanx for your reply.

Step 4 here:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
solved my prob.
But thanx a lot.

---

