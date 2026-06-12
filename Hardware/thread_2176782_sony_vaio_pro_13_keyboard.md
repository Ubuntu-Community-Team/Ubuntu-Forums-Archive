---
title: "sony vaio pro 13 keyboard"
date: 2013-09-26
forum: Hardware
---

### Post by shyamsg on 2013-09-26
I am running 13.10 on a new sony vaio pro 13. I am having a lot of trouble with the keyboard layout. 
The layout in the region and language settings looks like pc-105 and due to this a lot of the keys are 
mismapped. The right side of the keyboard functions like a numpad. Another quirk is that when i press
down the fn key, most of the keys work as they are supposed to. I have tried going through the 
various layouts that are there for english in the input sources list, but to no avail. Any help is much
appreciated.

Shyam

---

### Post by shyamsg on 2013-09-27
So I gave up and installed ubuntu 13.10 beta on the laptop and it seems to detect the keyboard just fine. Have no clue what happened. If I figure something out, I will post an update to this thread.

Shyam

---

### Post by pkinnaird on 2013-10-15
if you use the assist boot and move around a bit in the bios, then exit and choose 'exit and restart to windows' it will resolve this problem most of the time.

---

### Post by shyamsg on 2013-10-31
Thanks pkinnaird. That worked like a charm. I was also able to recreate the problem. It happens whenever the laptop shuts down due to critically low power - like full battery drain. This resets the keyboard layout to the unusable pc-105. Any insights as to why this happens is much appreciated. 

Shyam

---

### Post by alan-e-hensley on 2013-12-02
Confirmed that this issue is still present in 13.10 release. The issue persists through reboots even into another OS for me. For the record, my battery died while the laptop was suspended, not while on, so watch out for that.

The boot into bios and reboot trick worked though! Thanks for that!

---

### Post by wpieterson on 2014-01-02
I'm having the same issue. 13.10 installs fine works well for a while but after shut down due to drained battery the keyboard mapping is skewed. Fiddling with the bios resolves it. Kinda annoying but at least there's a work around.

---

