---
title: "no sound makes me sad"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by fencepost on 2009-02-27
I have a relatively new Dell Inspiron 1525 laptop which for the first few weeks ran without issue. I installed or upgraded something and now the sound won't work.

I have spent many hours combing through similar posts, but to no avail, including these:
[http://linux.dell.com/wiki/index.php...4#Known_Issues](http://linux.dell.com/wiki/index.php...4#Known_Issues)
[http://linux.dell.com/wiki/index.php...Kernel_Upgrade](http://linux.dell.com/wiki/index.php...Kernel_Upgrade)

I have also tried reinstalling every ALSA and GStreamer related package using the Package Manager.

I'm relatively new to Linux but do have a minor clue. However, I need instructions for how to diagnose the problem as well as specific things to try. Here's what I know:

On a command line if I hit the backspace key I get a system beep - good stuff.

When I hit the volume control on the top panel, the first time I get:

    The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

The second time I get:

    No volume control Gstreamer plugins and/or devices found. 

#uname -a
Linux ninegy-ninegy 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

#speaker-test
speaker-test 1.0.15

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory

etc.

Any help is greatly appreciated...

---

### Post by dox_drum on 2009-02-27
Are you using Hardy or Intrepid?

If you are using eiher one of them try
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=4928900[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4928900")

---

