---
title: "Creative mp3+ usb soundcard on ubuntu"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by ben82 on 2005-07-24
Hello,


does anyone know how to run a Creative soundblaster mp3+ usb card on Hoary? By default, alsa uses my built-in sound card. I can change this to the usb device in xmms, for instance, but the output is very jittery. I googled a lot and went on to testing the device before making it the default one; there seem to be some problems:

root@ben:/lib/modules/2.6.10-5-386/kernel/drivers/input # aplay -D plug:front:1 /tmp/test.wav
ALSA lib confmisc.c:980:(snd_func_refer) Unable to find definition 'cards.USB-Audio.pcm.front.0:CARD=1'
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3932:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM front:1
aplay: main:508: audio open error: No such file or directory

while the same command with "plug:front:0" would perfectly play the file using my built-in soundcard.

I also would like to make it my default sound card, as many programs do not allow you to select the output device.


I would be grateful if you could give me a hint...TIA!

Regards,

-br

---

### Post by jmclaug on 2008-03-14
Have you had any luck?

---

