---
title: "Audio problem with Toshiba Satellite L650 (10.04)"
date: 2011-05-29
forum: Hardware
---

### Post by MrZarq on 2011-05-29
Yesterday, I installed Ubuntu 10.04 on a Toshiba Satellite L650. After the installation, my sound worked correctly. After some fiddling to get the internet to work, I installed all the updates.

After the updates were installed (which included a new kernel), plugging in the headphones didn't mute the speakers anymore. The sound-quality however was still splendid. I Googled a bit and found that this could be solved by installing some alsa drivers. I did this, with the following command:

> sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update; sudo apt-get install linux-alsa-driver-modules-$(uname -r)This had the desired effect, but now the sound quality is horrible. It stutters and echoes.

I haven't deleted the old kernel yet, and when I tested it, the sound still worked correctly in that one.

Should I remove the new kernel and update again via the old kernel (if this is possible?) and then try fixing it some other way? Or are there some thing I can try with this kernel?

PS: [SIZE=2]lspci -v | grep -i audio[/SIZE]
returns
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

edit: update, I removed the new drivers I installed and now the sound quality is good again, but the headphones don't mute the speakers anymore

---

