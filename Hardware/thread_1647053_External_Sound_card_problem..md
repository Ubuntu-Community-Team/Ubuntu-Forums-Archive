---
title: "External Sound card problem."
date: 2010-12-16
forum: Hardware
---

### Post by Trueill on 2010-12-16
Hey ,

I have 2 sound cards.One on my onboard and other is external sound card.When i played an audio file i found that my audio is on steroids.Super fast ! then after installing vlc player and disabling my onboard soundcard from the bios i found that the audio is skipping.Can you guys please help me out ? 

Im a linux virgin.Installed it today.

---

### Post by Trueill on 2010-12-16
```
nuv@nuv:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2010-12-17 05:20:40--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 212.20.107.51
Connecting to www.alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2010-12-17 05:20:40--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 27026 (26K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,026      30.7K/s   in 0.9s    

2010-12-17 05:20:42 (30.7 KB/s) - `alsa-info.sh' saved [27026/27026]

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : 

```

---

