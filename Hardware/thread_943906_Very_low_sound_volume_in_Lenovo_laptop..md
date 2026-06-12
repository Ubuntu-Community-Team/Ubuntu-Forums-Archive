---
title: "Very low sound volume in Lenovo laptop."
date: 2008-10-10
forum: Hardware
---

### Post by october1917 on 2008-10-10
Hello.

I have Ubuntu 8.04 installed in a Lenovo Thinkpad R61i. The info about my card are the above:

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20549 (Venice)
```

I have very low sound volume compared to which i had have in Vista.

I followed step by step the instructions found on [this link]("https://help.ubuntu.com/community/HdaIntelSoundHowto") having already installed the last alsa and pulseaudio.

Unfortunately my model (CX20549) wasn't in the ALSA-Configuration.txt. Although i found the following information:

> I know CX20549 (Venice) is the same as CX5045 because if you go here, and search for 20549: [http://www.alsa-project.org/main/index.php...4rc2_v1.0.14rc3](http://www.alsa-project.org/main/index.php...4rc2_v1.0.14rc3)
you will find:
hda-codec - More fixes for Conexant HD Audio support

Renamed Conexant 5045 to CX20549 (Venice) per Conexant Documentation
Renamed Conexant 5047 to CX20551 (Waikiki) per Conexant Documentation
Fixed automute on HP Laptops with CX20551 codec.
Fixed recording issues on Toshiba Satelite P100/P105 series laptops
Added HP DV8000, DV2000Z, Fujitsu Si1520 support in [this link]("http://ubuntuforums.org/archive/index.php/t-784597.html").

If i understand it right that means, that i have to search in ALSA-Configuration.txt for Conexant 5045 and not for CX20549 which is my model:
> Conexant 5045

laptop        Laptop config
test          for testing/debugging purpose, almost all controls can be adjusted.  Appearing only when compiled with $CONFIG_SND_DEBUG=y

So i added to the end of the file /etc/modprobe.d/alsa-base the following line
```
options snd-hda-intel model=laptop
```.

I rebooted, but the low volume remains.

All switches of alsamixer volume control are in max. The same with pulse audio (paman and pavucontrol).

The sound preferences (System-->Preferences-->Sound) are all in PulseAudio Sound Server option, but i have already tried Alsa and Conexant Digital with no result. The Default Mixer Device is set to HDA Intel (Alsa Mixer).

I think i provided a lot of data. Is there some idea about what to do to fix the volume?

Thank you.

---

