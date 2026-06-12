---
title: "/dev/dsp: No such device"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by njs12345 on 2005-03-20
As the title says, my sound just disappeared during an update in the past few days.. I can't remember changing any of the sound-related files, so I think an update must have broken it.

```

$ esd
/dev/dsp: No such device
$ cat /dev/urandom > /dev/dsp
bash: /dev/dsp: No such device
$ sudo modprobe snd_pcm_oss
$ esd
/dev/dsp: No such device

```

And finally, an lsmod:

```

$ lsmod | grep snd
snd_intel8x0           32352  1
snd_ac97_codec         74144  1 snd_intel8x0
snd_usb_audio          65248  3
snd_pcm_oss            52132  0
snd_mixer_oss          19680  5 snd_pcm_oss
snd_pcm                94696  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_osssnd_timer              25060  1 snd_pcm
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
snd_usb_lib            12480  1 snd_usb_audio
snd_rawmidi            24480  1 snd_usb_lib
snd_seq_device          8460  1 snd_rawmidi
snd                    55012  9 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
soundcore              10016  5 snd
usbcore               118968  6 snd_usb_audio,snd_usb_lib,pwc,ehci_hcd,uhci_hcd

```

I've noticed a couple of other people with this problem, but no-one has posted how to fix it yet, or their solutions don't work for me :(

EDIT: Interestingly enough, mplayer can play sound - and it's always hung on the alsa-init part before. It looks like it's using SDL for sound:

```

SDL: Samplerate: 44100Hz Channels: Stereo Format Signed 16-bit (Little-Endian)
AO: [sdl] 44100Hz 2ch Signed 16-bit (Little-Endian) (2 bps)
Building audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...

```

---

### Post by Thief- on 2005-03-20
I'm having a similar problem with the Hoary update, but I get this:

 $ esd
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd/socket
This socket already exists indicating esd is already running.
Exiting...


No sound at all.

---

### Post by ubuntu-geek on 2005-03-20
Welcome to hoary sound hell.. This might help you out.

[http://ubuntuforums.org/showpost.php?p=100610&postcount=7](http://ubuntuforums.org/showpost.php?p=100610&postcount=7)

---

### Post by njs12345 on 2005-03-21
[QUOTE=ubuntu-geek]Welcome to hoary sound hell.. This might help you out.

[http://ubuntuforums.org/showpost.php?p=100610&postcount=7](http://ubuntuforums.org/showpost.php?p=100610&postcount=7)[/QUOTE]
 The funny thing is, I don't have an audigy2 card - I have an intel8x0 card. Still, I'll try what you said, thanks a lot :)

EDIT: It worked! Woohoo! You might want to add "intel8x0" to the list of card drivers you want to be compiled =)

---

### Post by Georges on 2005-04-04
I have also "suddenly" no sound after an upgrade, but I guess this may be why:

The kernel has been upgraded, but I was still booting on the previous one.

I keep you posted after I change grub, need to wait for my transcode to finish...
Georges

---

### Post by Georges on 2005-04-06
It had nothing to do with which kernel is running.
I confirm: I had to do above installation of the alsa driver, now sound is working.

This was for an Ensoniq 5880 AudioPCI (soundblaster)

Georges

---

