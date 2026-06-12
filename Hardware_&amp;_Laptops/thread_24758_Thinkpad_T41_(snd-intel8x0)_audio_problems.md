---
title: "Thinkpad T41 (snd-intel8x0) audio problems"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by littleking on 2005-04-08
heya, im new to ubuntu, just installed last night, very impressed though!

having a problem getting any sound though, tried xmms, totem, cdplayer, etc..

under volume control i have tried both ALSA & OSS, under multimedia system selector i have tried OSS, ALSA, ESD all with no avail. i have re-installed/configured alsa-source 1.08 with help from crimsun (from irc #ubuntu) have made sure that none of the settings were muted, with 1.08 i disabled master mono, enabled ex amp and mic line detect or whatever its called.

spent about 3 hours on this, im running the latest kernel, 2.6.10 or something... again im new to this so sorry for any inaccuracies..

anyone have any ideas?

---

### Post by littleking on 2005-04-08
i also found that when configuring xmms under alsa it shows hw:0,0 and hw:0,4 but under alsa, alsamixer -c0 works fine however alsamixer -c4 does not (tried c1-c10) to see if maybe ubuntu detected multiple soundcards, also cat /proc/asound/cards only shows the single i8x0 card

---

### Post by littleking on 2005-04-08
bump

---

### Post by Jezze on 2005-04-08
I had problems with snd-intel8x0 and solved it by blacklisting snd-intel8x0m (the modem if im not mistaking) in the /etc/hotplug/blacklist ... you can check if the snd-intel8x0m exist there, if not you could try to add it!

---

### Post by littleking on 2005-04-08
blacklisted by default

---

### Post by littleking on 2005-04-08
had to:

chmod 777 /dev/dsp
then
chmod 777 /dev/dsp/*

ALL WORKING!!!!!

---

