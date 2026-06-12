---
title: "Sound disappeared after upgrade."
date: 2009-04-19
forum: Hardware
---

### Post by budde on 2009-04-19
Good day gents and ladies.

Today I ran in to one of my most annoying Ubuntu experiences so far. In an attempt to upgrade wine to the latest version I did a "sudo apt-get upgrade". It showed a bunch of packages, so I upgraded them all. Then it wanted me to reboot, so I did. After the reboot I had NO SOUND AT ALL. 

System -> Sound -> Sound playback says "HDA ATI SB ALC663 ANALOG (ALSA) (NOT CONNECTED)". When I run aplay it tells me no soundcard found.

aplay output:
```
chr@chr-laptop:~$ aplay -l
aplay: device_list:217: no soundcards found...
```

lpsci output:
```
chr@chr-laptop:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
```

dmesg output (don't know if it's relevant):
```
chr@chr-laptop:~$ dmesg | grep snd_
[   11.461142] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[   11.462777] snd_hda_intel: Unknown symbol snd_card_new
[   11.469770] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[   11.471407] snd_hda_intel: Unknown symbol snd_card_new
[   11.532198] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[   11.534404] snd_hda_intel: Unknown symbol snd_card_new
[   11.540091] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[   11.542231] snd_hda_intel: Unknown symbol snd_card_new
[   11.566559] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[   11.568248] snd_hda_intel: Unknown symbol snd_card_new
[   11.572569] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[   11.574210] snd_hda_intel: Unknown symbol snd_card_new
```

Has anyone else experienced this problem? Does anyone have any solution? If so I will be forever grateful!

I'm running 9.04 alpha 6 on an Asus laptop with AMD64 and ATI Radeon HD4650.

Cheers,
Budde

---

### Post by budde on 2009-04-19
Hah. More often than not you find the solution to your problem right after you make a post about it.

I solved my problem with the script from [http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137")

Hope that can help anyone with similar issues!

---

