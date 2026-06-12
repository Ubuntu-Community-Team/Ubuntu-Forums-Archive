---
title: "Alsa hp compaq 2710p needs reboot to work"
date: 2010-11-18
forum: Hardware
---

### Post by mabhobs on 2010-11-18
Hi,

I just installed xubuntu 10.10 and I am very happy. But I have a little problem. When I mute my soundcard, I need to unmute and then reboot in order for it to work again. There is also a message at the beginning of the boot indicating some alsa failures. Does anybody have any suggestions? Thanks in advance.

---

### Post by mabhobs on 2010-11-19
First I want to clarify that sound did not work after muting and then rebooting. The problem is still there, but I found out some more information. What happens is that when I mute Master via the buttons on the notebook and then reboot the PCM Control will be muted as well. The problem is that I cannot unmute via the notebook buttons but have to open alsamixer and unmute PCM, which works. Unmuting PCM can also occur through visual controls for the sound in xubuntu on the top right hand corner after switching the Mixer Track to PCM and then opening the xfca4-mixer via left click.

---

