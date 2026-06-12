---
title: "Problem with DAC (Audiolab 8200CD)"
date: 2013-11-28
forum: Hardware
---

### Post by a_guenther on 2013-11-28
Hi!
I'm new here, because I have a question. I have problems getting my CD-Player with build-in asynchronous USB-DAC running, it's an Audiolab 8200CD and I am using the latest Kubuntu (more or less standard sound settings, with Phonon).
Whenever I try to use it with the USB-in, I hear every couple of seconds loud clicks or pops, I tried using Amarok and foobar2000 (through WINE), with different file types and sampling rates, and I changed the bit depth in foobar, but all this was not changing much about my problem.

Any advice how to get it running? I would prefer using foobar, but if WINE is a problem, Amarok or any other player is fine as well.
Thanks!

---

### Post by tgalati4 on 2013-11-29
Try different USB ports.  Is the CD plugged into the same outlet as the PC?  If not, then make sure they share the same outlet.  It could be a ground loop causing electrical discharge.  What you are hearing may be the digital equivalent of "hum" at 50 or 60 Hz.

Does it happen when no music is playing?  Or does it happen all of the time, with or without music playing?

---

### Post by a_guenther on 2013-11-29
Hi, thanks for your answer! No, it's no net-humming (I know that, studied electrical engineering with acoustics...).
It happens only during playback, it is not continuous, only every couple of seconds a loud short pop-sound (not really a beep). Different USB-plugs change nothing. It might change a bit how often it occurs when I change the bit depth, but not completely sure about this (and not sure if it happens regularly or not).

I think it must have something to do with the drivers or sound setting, but no idea...

Just to let you know: It's an Dell Inspiron 6400 (about 8 years old...), and the CD-player/USB-DAC is this one: [http://www.audiolab.co.uk/ProductDetail.aspx?lang=En&Tab2=8200CD](http://www.audiolab.co.uk/ProductDetail.aspx?lang=En&Tab2=8200CD)

---

### Post by a_guenther on 2013-11-29
Just tried to analyse it a bit further: the noises are definitely not regularly, not only the pop-sounds, also some crackling.

Just thought I had solved the problem using this: [http://ubuntuforums.org/showthread.php?t=1939711](http://ubuntuforums.org/showthread.php?t=1939711) (method 1, set to 44.1 kHz/16bit). Sound was in the 1st moment fine with foobar, but I realised the cracking noise occurs when I change a browser tab or (really strong) when I scrolled through foobar's playlist (but even though the computer is old, is not running on full power...). Thought it might be related to WINE, so I tried to use Amarok, but I could not get it running through the DAC: I chose the DAC as the soundcard in Phonon (testsounds seemed to work through the DAC), but when I was playing in Amarok it was only playing through the Laptop's build in speakers and Phonon was jumped back to the build in soundcard. So I might have overseen a setting in Amarok directly? (Foobar has an own selection which soundcard to use, which worked beside the noises...)
Similar behavier in VLC, beside that this time Phonon was not jumping back but seemed to ignore the setting in Phonon and played through the build in speakers....

So, I seem to have a problem to get the DAC working with Amarok or VLC (guess this is a simple setting which I might oversee?), and could then check if the noises still appear or if it is just a WINE/foobar-problem... even though I love foobar, I would be happy to get it at least running with Amarok without any noises...

---

### Post by a_guenther on 2013-12-01
Has anyone an idea?

I try to go analyse it a bit more systematic (but since I'm not a linux expert, just trying out what some ubuntu-sound-problem-FAQs tell me...)

1. The DAC is recognized (since I can play music, this was anyways expected):
```
cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfffc000 irq 44
 1 [Series         ]: USB-Audio - Audiolab 8200 Series
                      Lakewest Audio Audiolab 8200 Series at usb-0000:00:1d.2-1, full speed

```

2. When I use ```
 aplay /usr/share/sounds/alsa/Front_Center.wav 
```, the file is played through the build in speakers, also when I have the Audiolab selected in Phonon. But in Phonon I can play the test sounds...

Mh, and then I find many details about ALSA and Phonon, but I have no real idea... Here (German) [http://wiki.ubuntuusers.de/Sound_Problembehebung?highlight=soundkarte#Hilfestellung-bei-Soundproblemen](http://wiki.ubuntuusers.de/Sound_Problembehebung?highlight=soundkarte#Hilfestellung-bei-Soundproblemen) I find something what could fit, an "interrupt problem", they recommend to switch off HPET or change something in GRUB. No idea....

I found this [http://wiki.ubuntuusers.de/Sound_Problembehebung/Audio-Fehler-Beschreibung](http://wiki.ubuntuusers.de/Sound_Problembehebung/Audio-Fehler-Beschreibung) list to describe my audio setup as good as possible, so I will do this, maybe someone can find something in this?
```

~$ lsb_release -d
Description:    Ubuntu 13.10

~$ uname -r
3.11.0-13-generic

~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfffc000 irq 44
 1 [Series         ]: USB-Audio - Audiolab 8200 Series
                      Lakewest Audio Audiolab 8200 Series at usb-0000:00:1d.2-1, full speed

~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: STAC9200 Analog [STAC9200 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: STAC9200 Digital [STAC9200 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Series [Audiolab 8200 Series], Gerät 0: USB Audio [USB Audio]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

~$ aplay /usr/share/sounds/alsa/Noise.wav
Wiedergabe: WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono
(plays back through build-in speakers)

~$ lspci -nnk | grep -iA2 audio
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
        Subsystem: Dell Device [1028:01bd]
        Kernel driver in use: snd_hda_intel

~$ ps -C esd
  PID TTY          TIME CMD

~$ ps -C arts
  PID TTY          TIME CMD

~$ ps -C pulseaudio
  PID TTY          TIME CMD
 1545 ?        00:14:44 pulseaudio

~$ grep "^audio" /etc/group | grep "$USER" | wc -l
0

~$ lsmod | grep "snd"
snd_usb_audio         119227  1 
snd_usbmidi_lib        24326  1 snd_usb_audio
snd_hda_codec_idt      44605  1 
snd_hda_intel          42658  4 
snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_pcm                89488  4 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  21 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd

~$ head -n 3 /proc/asound/card0/codec#0
Codec: SigmaTel STAC9200
Address: 0
AFG Function Id: 0x1 (unsol 1)

~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head: »/proc/asound/card0/codec97#0/ac97#0-0“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden
(=> not found)

~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs
head: »/proc/asound/card0/codec97#0/ac97#0-0+regs“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden
(=> not found)

~$ cat ~/.asoundrc
~$ cat ~/.asoundrc.asoundconf
~$ cat /etc/asound.conf
=> give all not found...

```

Hope that helps somehow?

---

### Post by a_guenther on 2013-12-08
anyone an idea?

---

### Post by Findlay_Mistray on 2014-03-25
Hello, it is likely the high levels of jitter on the digital input to your [Audiolab 8200CD player]("http://www.hifigear.co.uk/audiolab-8200cd-cd-player-with-digital-inputs.html") is causing the dAC section to loose lock - you need to set the 8200CD to high bandwidth setting - see your user manual for more details.:p

---

