---
title: "Intel Soundcard Not Recognized on 9.04 on a Thinkpad"
date: 2009-08-13
forum: Hardware
---

### Post by Shidash on 2009-08-13
[FONT=Verdana]Hello,
I am new to Ubuntu and I have been trying to solve this problem for several hours now with no luck. I have gone through all sorts of tutorials and tried modifying /etc/modprobe.d/alsa-base. Some of the things that I have attempted the most are at the following links:
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)
[http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel](http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

The first two yielded no results at all. In the third it appears that my soundcard is not recognized by the system as when I type aplay -l, it tells me that no soundcards are installed.[/FONT][FONT=Verdana] Also, when I type lspci -v | less, it does not come up on the list of hardware. I know that I have a soundcard and it works just fine on XP.

Here is some information on my soundcard: [http://www.alsa-project.org/db/?f=53070191af536f45b47fcd55d4c837633a9a656a](http://www.alsa-project.org/db/?f=53070191af536f45b47fcd55d4c837633a9a656a)

Please help, I have no idea what to do.
[/FONT]

---

### Post by Shidash on 2009-08-13
After looking at this a bit more, I think that it might be a driver problem. I have no idea how to go about solving a driver issue. Any ideas?

---

