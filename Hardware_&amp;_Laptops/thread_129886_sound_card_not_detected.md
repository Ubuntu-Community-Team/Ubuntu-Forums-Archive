---
title: "sound card not detected"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by tanman on 2006-02-14
I have just finished installing ubuntu on a older computer that was running windows
98. Everything went well except for the sound.
On the seaker in the top right of the screen has a little "x" by it. When I click on the speaker icon I get this message

The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

the sound worked well in 98 before I installed ubuntu. I can not find a command for the gstreamer or how to check for plugins. I am very new to linux so any help would be great. Thanks

---

### Post by bountonw on 2006-02-14
I just had my sound problems solved here.  Hope that it helps.

[http://www.ubuntuforums.org/showthread.php?t=129246](http://www.ubuntuforums.org/showthread.php?t=129246)

---

### Post by tanman on 2006-02-14
well I put this command in the terminal

lsmod | grep snd

and I recieved this reply

snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
user@ubuntu:~$ sudo modprobe snd-intel8x0
user@ubuntu:~$ lsmod | grep snd
snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

I have no idea what any of that means

I have also went in and applied all the gsreamer codecs from the synaptec package manager

---

