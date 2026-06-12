---
title: "No audio after 10-jun security update"
date: 2019-06-11
forum: Hardware
---

### Post by leoszt on 2019-06-11
After yesterdays's security updates (10/7/19) I got my system's audio messed up.

**SYSTEM INFO:**

Kubuntu  18.04.2 LTS x86_6480YH
Lenovo ideapad 320-15IKB
4.18.0-21-generic

**ALSA INFO**

[http://alsa-project.org/db/?f=08f3c96bf88fc389bc6d947a3a779d59001334bb](http://alsa-project.org/db/?f=08f3c96bf88fc389bc6d947a3a779d59001334bb)

**I've already tried all of this:**

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#heading=h.iyf5tyf0d8tb](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#heading=h.iyf5tyf0d8tb)
(except Nvidia method, since I dont have no such card)

any help is appreciated, thank you


[HR][/HR]

additional info:

I used my system normaly for some hours after updating, then went AFK for like 1 hour and when I came back there were several APP crashing reports, like 20 of them. They were all about **latte dock** and system was awfully irresponsive, with "**pulseaudio**" clogging up like 30% of my processing.

_I deleted pulseaudio's config and had it uninstalled_. 

```
$ rm -rf ~/.pulse* ~/.asound* ~/.pulse-cookie
$ sudo apt-get remove --purge alsa-base pulseaudio
```

Oddly enough, latte was uninstalled altogether. System was finally ok, had the processor chilled for once.

_Them I reinstalled alsa and pulseaudio, and I've got no audio since then._

The weird part is that in system settings my sound card is recognized, everything seems to be set up, I just dont get any audio out.

I also have got no tray audio Icon.

---

