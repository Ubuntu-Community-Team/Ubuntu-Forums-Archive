---
title: "[SOLVED] no sound in new 8.04 installation - nvidia hda"
date: 2008-07-21
forum: Hardware
---

### Post by dimitris78 on 2008-07-21
Hello,

I don't get any sound from my laptop (Medion MD 96282), which has a MCP51 High Definition Audio device from nVidia corporation. Ubuntu can find the chip, has the drivers but there is no sound at all! Nothing is muted in volume control and I tried the basic troubleshooting in the wiki 'debugging sound problems' and the 'Comprehensive Sound Problem Solutions Guide v0.5e' in the ubuntu forums: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
with no results. Maybe I'm doing something wrong since I am a newbie ubuntu user. Any suggestions?

Thanks in advance, D.

---

### Post by dimitris78 on 2008-07-29
Solved, with some help from the alsa-user mailing list.
I had to add: 
options snd-hda-intel model=gateway
to the /etc/modprobe.d/alsa-base file

---

