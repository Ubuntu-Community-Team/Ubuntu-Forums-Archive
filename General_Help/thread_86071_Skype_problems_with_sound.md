---
title: "Skype problems with sound"
date: 2005-11-04
forum: General Help
---

### Post by ovidiusoft on 2005-11-04
I just installed skype (took the tar.bz with the statically linked Qt version from Skype.com) and I can talk (the other party hears me perfectly) but all I can hear are some cracks :(. Anyone had this issue?

I run 5.10 on a Acer TravelMate 2500 laptop. I killed esd before running Skype, no other application is using the sound devices (i hope).

# lspci | grep Audio
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller

# lsmod | grep snd
snd_atiixp_modem       15396  0
snd_atiixp             18912  1
snd_ac97_codec         72188  2 snd_atiixp_modem,snd_atiixp
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  9 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  3 snd_atiixp_modem,snd_atiixp,snd_pcm

---

### Post by ozorba on 2005-11-04
[QUOTE=ovidiusoft]I just installed skype (took the tar.bz with the statically linked Qt version from Skype.com) and I can talk (the other party hears me perfectly) but all I can hear are some cracks :(. Anyone had this issue?

I run 5.10 on a Acer TravelMate 2500 laptop. I killed esd before running Skype, no other application is using the sound devices (i hope).
[/QUOTE]

I got this from this Forum but cannot find the reference to it now.
[QUOTE="From Ubuntu Forum"
Hello there,
This is just a clean and better organised guide of varunus's HowTo located here. So primarily all the credits go to him.

This HowTo will give you instruction on enabling software mixing, to avoid application problems like Audacity needing killall esd to work as well as Skype [now Skype will no longer crash if you receive a message or a call (when it try to play sound in fact)], so let's get to work shall we ?? .
1.We need to install libesd-alsa0 so
Code:

sudo apt-get install libesd-alsa0

2.We need to create /etc/asound.conf, so
Code:

sudo gedit /etc/asound.conf

Insert into it:
Code:

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
period_size 2048        #1024
buffer_size 32768       #4096
                        #periods 128
rate 48000              #44100
}
bindings {
0 0
1 1
}
}

3.We need to change /etc/esound/esd.conf contents so:
Code:

sudo mv /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf

Insert into it:
Code:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

4.Now You need to change ubuntu sound server to alsa (you can leave it ESD but better use alsa because it has better sound handling):
Code:


gstreamer-properties

Change both (in the Audio Tab not the Video) from ESD to ALSA so it looks just like the picture:

All that's left now is to restart your computer (after restart you must hear sound) to enable these changes. Also configure XMMS or Beep-media-player (or any player) to use ALSA instead of eSound/ESD. If you hear a strange sound, just change everything back to ESD. If everything worked correctly, now Audacity & Skype will work normally and all the program will play sound using either Alsa or ESD.
Correct beep-media-player configuration:

* If you couldn't play any sounds using ALSA then your /etc/asound.cond & /etc/esound/esd.conf needs some more advanced tweaking (or your sound card just won't support it).

* The codes above are to be done inside a terminal window.

Thanks to varunus for the original HowTo and to Vaportrail for the correct /ets/asound.conf contents.

Enjoy everyone . 
[/QUOTE]

Cheers,
OZ

---

### Post by ovidiusoft on 2005-11-09
Thank you for your answer, unfortunatly it doesn't work :(. There must be something wrong with my sound card or something... I'll keep digging.

---

