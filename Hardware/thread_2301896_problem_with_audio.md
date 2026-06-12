---
title: "problem with audio"
date: 2015-11-06
forum: Hardware
---

### Post by luca-barazzuol on 2015-11-06
Hi, I have just installed U15.10 (x86_64. Everything has worked well but, after few days, audio suddenly disappeared.

I've tried the common procedure to reinstall the audio server but without success:
```

sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

```

Here is my hardware description:
```

$ LC_ALL=C cat /proc/asound/card*/codec#* | LC_ALL=C fgrep --before-context=4 --after-context=1 "Subsystem Id"
Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100500
--
Codec: Realtek ALC892
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0892
Subsystem Id: 0x1458a002
Revision Id: 0x100302

```

If I check the sound configuration, the output tab is completely empty.

My CPU is an AMD A8-7600 Radeon R7 on a GA-F2A88XN-WIFI.

The weirdest thing is that at login time I can hear the typical sound.

What could be the problem?


LuKe

---

### Post by Vinayaka_Negalur on 2015-11-06
You can quickly check this by using "arecord" (and record some audio) and "aplay" to listen.
You may have to check the parameters of arecord as per your configured sound card.

"arecord -d 2 -f S16_LE -r 16000 -D plughw:1,0 sample.wav"
"aplay sample.wav"

to increase the volume boost
-----------------------------
sudo apt-get install pulseaudio
pactl -- set-sink-volume 0 150%

---

### Post by luca-barazzuol on 2015-11-06
I don't think the problem is about the volume.
Here is the output of the aplay command:
```

$ arecord -d 2 -f S16_LE -r 16000 -D plughw:1,0 sample.wav
Recording WAVE 'sample.wav' : Signed 16 bit Little Endian, Rate 16000 Hz, Mono
luke@microPC-luke:~$ aplay sample.wav
ALSA lib pcm_dmix.c:1024:(snd_pcm_dmix_open) unable to open slave
aplay: main:722: audio open error: No such file or directory

```

LuKe

---

### Post by Vinayaka_Negalur on 2015-11-06
If arecord does not give any error, then mic should be working fine. to  confirm this, play the file "sample.wav" in any player that is available  in host machine.

For aply, you can refer to [https://bbs.archlinux.org/viewtopic.php?id=173709](https://bbs.archlinux.org/viewtopic.php?id=173709)

---

### Post by Vinayaka_Negalur on 2015-11-06
Check ```
 cat /proc/asound/cards 
``` response. The result of this command should tell you which number to be used with plughw parameter of arecord.
The above comamnd tells where the hardware number of the sound card installed.

---

### Post by luca-barazzuol on 2015-11-06
Playing the sample gives me this error:
[I]"The audio playback device HD-Audio Generic (ALC982 Analog) does not work. Falling back to Default."
[/I]
Here the ouput of cat /proc/asound/cards

```

$  cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeb64000 irq 42
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb60000 irq 16

```

LuKe

---

### Post by luca-barazzuol on 2015-11-07
I think I solved.

Probably there is a bug in pulseaudio-equalizer. I purged it and sound has come back!

The problem now is: how can I equalize my audio?

LK

---

