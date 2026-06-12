---
title: "missing alsa driver help"
date: 2011-11-25
forum: Hardware
---

### Post by S_p_or_t_o on 2011-11-25
I'm having sound issues on my Clevo B7130 laptop

ubuntu 10.04 LTS lucid

```
$ uname -r
```
```
2.6.32-35-generic-pae
```

the bug for me is no microphone through the mic rca input, speakers work fine as well as USB devices.

following the troubleshooting doc i ran the command and it returned:
```
 cat /proc/asound/card0/codec* | grep Codec
```
```

Codec: VIA ID 448
Codec: Intel G45 DEVIBX

```

I've read that the VIA codec means that alsa is confused or partially working. to fix it, i tried the following commands:

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

it returns the following error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-35-generic-pae
```

Can anyone direct on how to resolve my issue? 
Is there a driver available that i could compile?

---

### Post by S_p_or_t_o on 2011-11-25
I came across a backport in synaptic

"linux-backports-modules-alsa-2.6.32-35-generic-pae"

installing it didn't change anything though.

---

### Post by S_p_or_t_o on 2011-11-25
i followed compiling my own drivers from [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), but i get the following errors with ```
sudo make
```

```
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1

```

---

### Post by S_p_or_t_o on 2011-11-25
i tried the help from [http://ubuntuforums.org/showthread.php?t=1885240]("http://ubuntuforums.org/showthread.php?t=1885240") and got a microphone input selector after following it. the sound quality is lessened a bit (more static in the speakers), but there is more instuctions for me to follow.

I did get the same error stating my kernel's driver could not be found, wondering if it defaulted to the back port...

---

### Post by S_p_or_t_o on 2011-11-30
just discovered my movie player doesn't have sound through my speakers after following the steps in the help guide, same with VLC. pulseaudio volume control should the app it sending sound but i got nothing. Sound goes through the speakers when it comes from a web browser  :/

it's like LTS support is waning, i'm considering a different distro - anyone else reading this with this problem should do the same. 

I realize it's free, but long term support was promised and i was hoping for better from ubuntu

on the troubleshooting guide, i think it fails on supported versions of ubuntu (see original post)

---

### Post by S_p_or_t_o on 2011-11-30
re-ran the script in step one of the troubleshooting procedures and got the speakers back #-o

i'm pretty sure than my sound driver is the backport

this whole kernel update has been maddening

---

