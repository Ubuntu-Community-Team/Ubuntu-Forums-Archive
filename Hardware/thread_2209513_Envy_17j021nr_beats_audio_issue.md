---
title: "Envy 17j021nr beats audio issue"
date: 2014-03-06
forum: Hardware
---

### Post by wbatten1 on 2014-03-06
Yep, it's that 'my subwoofer and rear speakers don't work' thread again...

I've tried adding options ```
snd-hda-intel model=rev
``` to /etc/modprobe.d/alsa-base.conf and it didn't work.

I've also installed alsa-tools-gui and ran hdajackretask.  I remapped 0x0d, 0x0f, and 0x10 to internal speaker, internal speaker, and internal speaker (LFE), respectively.  I wasn't able to apply the changes at first, but by typing ```
ln -s .config/pulse/ .pulse
``` in the terminal, I was able to.  Applying the changes made all of my sound go away.  When I went into my sound settings, I saw that there was nothing in the "Play sound through" section.  I tried all sorts of different configurations with unconnected pins, but they all ended with the same result. After closing hdajackretask and removing the symlink by typing ```
rm -r .pulse
``` I'm able to see "Speakers, built-in-audio" again in my sound settings.  My front speakers started working again after a few minutes of idle time.  Unfortunately, the sound icon on the top right of the workspace is gone, even after rebooting several times.

Can anyone help me in solving the mystery of making all my speakers work?  I'm not too concerned about the sound icon... I'm planning on doing a fresh install once I (you) figure this out.

Thanks in advance.

---

### Post by wbatten1 on 2014-03-07
bump

---

### Post by wbatten1 on 2014-03-08
Is there any other information I might be able to provide in order to better my chances of getting a response?

---

### Post by wbatten1 on 2014-03-09
bump

---

### Post by wbatten1 on 2014-03-10
Are there any ideas where I could start looking?...

---

### Post by wbatten1 on 2014-03-20
bump :(

---

### Post by wbatten1 on 2014-05-05
Okay, so do people exist on this forum or is it simply automated?  I came here for assistance, not to see what being ignored feels like.  Perhaps you don't have the exact answer... that's fine!  How about where to start looking?  How about referencing some areas for me to possibly explore?  How about a simple "I don't know?"  Come on people...  Communicate so we can solve this problem.

---

### Post by Yellow Pasque on 2014-05-05
Sound issues are tough.

Give the ALSA info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
(Make sure you remove customizations from /etc/modprobe.d/alsa-base.conf before running the script.)

---

