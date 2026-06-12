---
title: "Sound problems"
date: 2004-10-23
forum: Hardware &amp; Laptops
---

### Post by Julius on 2004-10-23
I have just installed Ubuntu (and I LOVE IT) but I have a little sound problems :(

The sound of the start keeps looping all the time. Right now I have turn my volume off just not to listen to it (sounds like drums or something). 

My lsmod

$ lsmod
Module                  Size  Used by
[...]
snd_via82xx            26660  4
snd_ac97_codec         59268  1 snd_via82xx
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  3 snd_via82xx,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_via82xx,snd_pcm
gameport                4736  1 snd_via82xx
snd_mpu401_uart         7296  1 snd_via82xx
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  12 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
[...]


I have found out that the problem is realted to esound (esd).

---

### Post by Julius on 2004-10-24
OK I finally killed the sound.
This is what I get typing the command
sudo ps -ax

...
 3625 ?        Ss     0:00 /bin/sh /usr/lib/gdmplay /usr/share/sounds/question.w
 3626 ?        S      0:00 /usr/bin/aplay -q -N /usr/share/sounds/question.wav
...

Killing the 3626 process will stop the sound. After this, I can play music cds fine, but I still have problems because every wav that sounds will loop (7 times, to be accurate). 

:(

---

### Post by Julius on 2004-10-25
Update:

-> The soundcard I use is VT82C686 AC97 (it came with the motherboard).
-> I found out that the problem is related to ESD.  MP3s works fine with XMMs and GMplayer. That's because they use OSS Output [libOSS.so].
-> Other programs like Rhythm box use the ESD output. Thill will cause the first 1-2 seconds of the audio file to loop for ever. I know this because when an audio file played with Esound is looping, I can see esd in the list (sudo ps -ax). 
-> And this is the strangest thing: Other applications like Gaim or even GMplayer, when playing Wav audio files, they will play them correctly, but 7 times in a row! I had to disable sounds in Gaim because of this. There is no forever-loop, but it will play 7 times :( This happends using OSS too. In XMMs, the playback of Wav files is done properly.

What could be causing the problem? A misconfiguration of Esd, or a wrong sound driver? I have NO problems at all using Knoppix.


Thanks in advance!!

---

### Post by philip on 2005-01-17
I have the same problem but have not solved it yet.  For the time being I killall aplay after booting to keep question.wav from driving me nuts.  Perhaps I'll be able to let you know something more soon.
- ph

---

### Post by zixxer on 2005-06-29
i "fixed" the problem. i went to** /usr/share/sounds ** ran **mkdir disabled** and then **mv *.wav disabled** and then restarted the computer and the sound was no more...along with any other events that used the sounds that were in there. i dont care about the sounds so it works for me, and its permanent too, until you move the files back to the parent directory. This will stop the sound, but im pretty sure the system is still looking for it, could cause instability.


~brad

---

