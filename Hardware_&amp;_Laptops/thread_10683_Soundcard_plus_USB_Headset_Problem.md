---
title: "Soundcard plus USB Headset Problem"
date: 2005-01-10
forum: Hardware &amp; Laptops
---

### Post by Disorder2 on 2005-01-10
I have a fresh warty installation here and everything went like a breeze, sound, video, network....
Then I went to get a USB headset to use with skype.

What's happening now:
When I plug in my headset *after* system start I can see it shows in the Volume control but I can not use it with skype.

*** Update ****
I can use it with skype now.
But how the heck can I make all devices show up when I have the USB headset plugged in *before* boot?
I mean, not so nice crawling under the table every time I have to start my machine, right?
******************************************

When I plug it in *before* system boot then in the Volume control it's registered as "USB Audio class Driver [OSS Mixer]". Next to it I find "intel ICH5 [Alsa Mixer]" but I can't use it.
All sound comes through the crappy headphones - and I still can't use Skype.

What I want to do is just have the internal sound running as my primary device and use the USB Headset with skype (skype allows you to define the sound device to use).

None of the tutorials gave me any help. I mean I have Alsa installed apparently and with one device it worked out.

Any idea ?
Must be something with Alsa/oss magic, but what?
I can see that the USb headset is registered as an OSS device, the internal card as an ALSA device, and apparently the system prefers the OSS device, but how do I get out of this? Should be possible to have them both controlled by weither alsa/oss, right?

Oh - the usual questions:

ls -la /dev | grep dsp
crw-rw----    1 root     audio     14,  12 2005-01-10 12:49 adsp
crw-rw----    1 root     audio     14,   3 2005-01-10 12:49 dsp

(with an extra line of 
crw-rw----    1 root     audio     14,   3 2005-01-10 12:49 dsp1
if and only if I plug in the hedset *after* system boot)

Yes, I am in the group audio.

Yes, the USB device registers correctly because right now I'm listening to some mp3's through it.

And the modules:

> lsmod | grep snd
snd_intel8x0           35468  3
snd_ac97_codec         67844  1 snd_intel8x0
gameport                4608  1 snd_intel8x0
snd_mpu401_uart         7776  1 snd_intel8x0
snd_usb_audio          70880  0
snd_rawmidi            24704  2 snd_mpu401_uart,snd_usb_audio
snd_seq_device          8040  1 snd_rawmidi
snd_pcm_oss            52968  0
snd_mixer_oss          19456  1 snd_pcm_oss
snd_pcm                95140  3 snd_intel8x0,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11432  2 snd_intel8x0,snd_pcm
snd_timer              24900  1 snd_pcm
snd                    55300  16 snd_intel8x0,snd_ac97_codec,snd_mpu401_uart,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10112  7 snd,audio
usbcore               115684  7 snd_usb_audio,audio,usbhid,uhci_hcd,usb_storage

And my /etc/modules.conf reads
### update-modules: start processing /etc/modutils/alsa-base
above snd-pcm snd-pcm-oss

nothing else related to snd

---

