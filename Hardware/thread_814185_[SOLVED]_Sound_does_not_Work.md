---
title: "[SOLVED] Sound does not Work"
date: 2008-05-31
forum: Hardware
---

### Post by nealmohanp on 2008-05-31
I have an acer travel mate 8204WLMi andthe sound doesn't work. I have kubuntu 8.04 installed on it plz help

---

### Post by ugm6hr on 2008-05-31
Please post the output from the following:
```
lspci
lshw -C mulitmedia
amixer
```

Simple thing to try:
```
alsamixer
```
Maximise (arrow keys) AND unmute (M) everything.

---

### Post by Zorael on 2008-05-31
For the second code tag, I think he means **alsamixer**. :>

---

### Post by nealmohanp on 2008-05-31
it started working when i installed the kde 4.04

---

