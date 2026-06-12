---
title: "alsa volume control on multimedia keys"
date: 2011-10-23
forum: Hardware
---

### Post by chestnyh on 2011-10-23
Hello everybody!

I have Lubuntu 11.10 and I want to control volume on media keys. But I don't know how forced to work alsamixer with media keys.

I have already install:
```
sudo apt-get install alsa-utils alsa-base alsa-tools
```
And with obkey help on "XF86AudioRaiseVolume" key have a command "amixer -c 0 -q set Master 3%+ unmute". But nothing happening.
Also alsamixer in terminal works great.

How to solve this problem?

---

### Post by chestnyh on 2011-10-24
The problem was solved by changing a command. Instead "Master" must be "PCM"
e.g.
```
amixer -c 0 -q set PCM 3%+ unmute
```

Manual was helped. Sorry for simple question:)

---

