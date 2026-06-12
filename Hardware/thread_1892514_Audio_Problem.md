---
title: "Audio Problem"
date: 2011-12-08
forum: Hardware
---

### Post by Mexicosauce on 2011-12-08
Hi everybody,
i've got a problem with the audio of my pc (Ubuntu 11.10). Audio is not working at all even if the sound card is recognized (NVidia CK804), and yes i turned up all the volumes (including: aslamixer, gstreamer properties, and the normal volume on desktop).
I need help!

 

cacca@cacca-desktop:~$ lspci | grep -i audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22



AlsaMixer v1.0.24.2 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;     Scheda: NVidia CK804                                 &#9474;
&#9474; Processore: Realtek ALC850 rev 0                     &#9474;



cacca@cacca-desktop:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: CK804 [NVidia CK804], dispositivo 0: Intel ICH [NVidia CK804]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: CK804 [NVidia CK804], dispositivo 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0


cacca@cacca-desktop:~$ asoundconf-gtk

Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap»,

Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap»,

Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap»,

Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap»,
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

lsmod | grep snd
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  3 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  10 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm

---

### Post by Mexicosauce on 2011-12-08
EDIT: sound is working only with an usb external audio controller(out and in jacks). if i plug into the soundcard the output is extremely low, like a whisper, (only on one speaker) almost imperceptible.. Dont know what to do, please help!

---

