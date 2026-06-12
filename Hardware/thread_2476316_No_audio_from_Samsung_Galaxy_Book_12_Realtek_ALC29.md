---
title: "No audio from Samsung Galaxy Book 12 Realtek ALC298 (20.04.4)"
date: 2022-06-22
forum: Hardware
---

### Post by mistermeseeks on 2022-06-22
Hello folks! 

Got another problem with this device. First it is/was the WiFi not working at all (I've now been able to make it work for 5G but not 2.5g)

Now I have noticed that the AUDIO does not work. Apparently this problem has been unresolved in Ubuntu as the ALC298 device seems to be just as stubborn as the WiFi adapter. However I do see a light at the end of the tunnel as others have been successful in Manjaro with a "Samsung Galaxy Book". There are several "Samsung Galaxy Book" variants, and following the instructions FOR Manjaro on Ubuntu proved fruitless. 

[https://forum.manjaro.org/t/howto-set-up-the-audio-card-in-samsung-galaxy-book/37090](https://forum.manjaro.org/t/howto-set-up-the-audio-card-in-samsung-galaxy-book/37090)

There's definitely some wizardry going on in this post BUT in this post is a [SIZE=4]clue [/SIZE]to solving the issue..I  [SIZE=4]***[COLOR=#212121][FONT=Roboto]need to find the correct HDA Verbs for [/FONT][/COLOR]***[/SIZE][COLOR=#000000]/dev/snd/[/COLOR][COLOR=#ff0000]hwC0D0 (insert your file here) (in my case its hwC0D0 and hw C0D2) [/COLOR]

[https://github.com/ryanprescott/realtek-verb-tools/wiki/How-to-sniff-verbs-from-a-Windows-sound-driver](https://github.com/ryanprescott/realtek-verb-tools/wiki/How-to-sniff-verbs-from-a-Windows-sound-driver)

This is funny. So apparently I have to Install a virtual windows environment in Linux on a pc that has a working windows install. is there another way?

I also found this link here 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1851518](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1851518)

If anyone can assist me with this task I will give you many thanks!

I will be poking around to try to resolve the issue myself but as I am only about 1 month into working with Linux, I am a complete and total NOOB and progress will probably be slow. But, keep checking on this post and one day it may have [SOLVED] in the title.

Lets begin!

alsa-info output 

[https://pastebin.ubuntu.com/p/vNtQQjKVZV/](https://pastebin.ubuntu.com/p/vNtQQjKVZV/)

*************************************************************************************************************************************************************************************************************************************
```
sudo dmesg | grep audio                                 
[   28.302112] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   29.051379] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC298: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[   29.051386] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   29.051388] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   29.051391] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[   29.051392] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[   29.051393] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x18
[   29.051395] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
```

---

### Post by nzsx1xszn on 2022-06-30
hi, I have a Thinkpad L470, ALC298 codec. He has a similar problem. No sound comes from the speaker. But they work fine in Ubuntu 17.04. (I would like to solve this problem at the Linux kernel level) p.s google translate
[http://alsa-project.org/db/?f=ed01d35ac2f3b15a58a0b55062887f825680886e](http://alsa-project.org/db/?f=ed01d35ac2f3b15a58a0b55062887f825680886e)
+ everything works on BSD-based systems

---

