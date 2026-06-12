---
title: "Sound permissions problem"
date: 2004-12-09
forum: Hardware &amp; Laptops
---

### Post by ming0 on 2004-12-09
EDIT! after a reboot, things work??? ;)


I just did a fresh install of warty 4.10, and have had warty beta working w/ sound before--I'm using my old /home directory, but I don't think that's the problem. I can run alasmixer as sudo, but when I try as normal user I get:
```
dean@dim:/dev $ alsamixer
alsamixer: function snd_ctl_open failed for default: Permission denied
```
I've added myself to the audio group, and have the following permissions:
```
dean@dim:~ $ ls -l /dev/dsp /dev/audio
crwxrwxrwx    1 root     audio     14,   4 2004-12-09 00:43 /dev/audio
-rwxrwxrwx    1 root     root        20480 2004-12-09 01:22 /dev/dsp
```I assume that this is permissions related, but I can't figure out what to do :-s 

Oh, and just to taunt me--when I get to the GDM screen, I hear the drumbeats--so I know that everything is ready to work....

Thanks,
Dean

---

