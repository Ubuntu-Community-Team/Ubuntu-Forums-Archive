---
title: "No sound on all new linux distributions"
date: 2016-07-08
forum: Hardware
---

### Post by Sbininit on 2016-07-08
Hey guys! What's up with the no sound thing with all the new linux distros. It doesn't seem to matter what I try these days, there'll be no sound and bookmarks will not load from older backups. And usually I have this dummy output listed in the sound tab. And usually no matter what I try to fix sound it simply doesn't work.

No sound and no bookmarks. Both of those have all worked wonderfully until now. I can create new book marks but I can't load them all from backups. I find myself using an older version of Knoppix 6.2 because its the only linux I have sound and bookmarks on. I have it set as my default boot instead of Ubuntu 16.04.

---

### Post by howefield on 2016-07-09
Thread moved to the "*Hardware*" forum.

---

### Post by Sbininit on 2016-12-06
Hey folks! There is still no sound on my Ubutnu 16.04 install. The card is not recognized. Obviously the wrong driver is loading for the sound card. The card works fine in XP, Ubuntu 8.10 thru 10.04 without issue as well as all the old knoppix installs from 5.1 to 6.3.

 None of the latest linux kernels in Kali, Knoppix Ubuntu  or any other linux OS I've tried has working sound. 

If someone could help me get my card recognized and functioning I'd greatly appreciate it.

---

### Post by Yellow Pasque on 2016-12-06
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Sbininit on 2016-12-08
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)


Hello Temujin, I checked your link and followed the instructions and uploaded the file to alsa-project.

 Here is the link if you have a minute to look at it.  [http://www.alsa-project.org/db/?f=942c150e067f97c088d333c9a83d9fb55b1d7db3](http://www.alsa-project.org/db/?f=942c150e067f97c088d333c9a83d9fb55b1d7db3)

---

### Post by Yellow Pasque on 2016-12-09
Oh yeah. "no codecs initialized" is rough. I see you've already tried playing with probe_mask:
```
snd_hda_intel: probe_mask=1 model=auto
```

Maybe disabling the audio codec in the BIOS and rebooting, and then re-enabling will help? It worked for someone with a similar issue (and same Realtek ALC880 codec):
[https://ubuntuforums.org/showthread.php?t=2232882](https://ubuntuforums.org/showthread.php?t=2232882)

---

### Post by Sbininit on 2016-12-09
> **Temüjin said:**
> Oh yeah. "no codecs initialized" is rough. I see you've already tried playing with probe_mask:
```
snd_hda_intel: probe_mask=1 model=auto
```

Maybe disabling the audio codec in the BIOS and rebooting, and then re-enabling will help? It worked for someone with a similar issue (and same Realtek ALC880 codec):
[https://ubuntuforums.org/showthread.php?t=2232882](https://ubuntuforums.org/showthread.php?t=2232882)


Yes I've tinkerd with alsa-base.conf a bit and have gone throught several of the sound troubleshooting guides to no avail.  I see folks always suggest to add such and such line to the end of that list. Does being at the end give it priority over the other lines listed above that don't have the # beside them?

I'll try the BIOS thing and see if that helps. I think the new linux kernels must be written with the ALC880 not in mind.  In all previous kernels sound just simply worked. I've had a few hickups here and there but not many and when I did I could always find something on the Forums that would work but not this time.

---

