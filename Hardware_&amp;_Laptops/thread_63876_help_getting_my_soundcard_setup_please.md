---
title: "help getting my soundcard setup please"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by sal on 2005-09-09
i got an old sound card and stuck it in the system because i wanted to stop ussing the onboard sound.
this is the output of an sudo lsmod | grep snd:

snd_cs46xx             86472  1
snd_rawmidi            24480  1 snd_cs46xx
snd_seq_device          8460  1 snd_rawmidi
snd_ac97_codec         74144  1 snd_cs46xx
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  2 snd_cs46xx,snd_pcm
gameport                4448  1 snd_cs46xx

i have added snd_cs46xx to the /etc/modules file.

the sound works but i cant get the microphone to work with audacity.

I used Kmix to see if the mic was on and it was set. yet i cant get it to work to record audio or use skype. i know the port on the sound card is working because in kmix when i turned on the top green butten i was able to talk into the mic and here my self out of the speakers. but when i only enable the lower red button in kmix it wont let me record in audacity. 
in audacity both the playback and recording is set to /dev/dsp

one thing of note:
i followed this thread to get the sound card working:
[http://ubuntuforums.org/showthread.php?t=60533](http://ubuntuforums.org/showthread.php?t=60533)
as per the instructions to get rid of the /etc/asound.conf to get the card working and im woundering if thats playing a part in me not being able to get the mic to record. here is what my /etc/asound.conf looked like before i got rid of it:
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

also im woundering if i install
alsa-base_1.0.9b-4_all.deb
and
alsa-utils_1.0.9a-4_i386.deb

will it help fix alot of the ubuntu (with kubuntu-desktop) 5.04 sound problems.

any help in geting this rite will be appretiated. tia

---

