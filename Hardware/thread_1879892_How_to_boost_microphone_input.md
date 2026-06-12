---
title: "How to boost microphone input"
date: 2011-11-12
forum: Hardware
---

### Post by pedorro on 2011-11-12
I'm really trying to figure out how to boost microphone input.  I've seen advice ranging from 'Just turn it up' to 'get rid of pulseaudio'.  And there are posts going back several years, most of who's advice is out of date.  I'm just looking for a simple way to add a few dB to the mic gain, because it's definitely capturing below its normal level.

I've gone through all the inputs I can find in alsa with no help.  Is there something in pulseaudio that I can tweak?  I've got Intel integrated audio:
```
sean@Oberon:~$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
```Thanks in advance :)

kubuntu 11.10

---

