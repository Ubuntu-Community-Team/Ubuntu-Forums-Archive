---
title: "No sound"
date: 2008-08-14
forum: General Help
---

### Post by kelvinlokahong on 2008-08-14
I am very new to ubuntu and I've just installed. Everything turns out better than Window XP apart from the sound. I couldn't get any sound. Anyone can help.

---

### Post by null byte on 2008-08-14
System - Prefences - Sound

Make sure everything is set to ALSA.

Also, double click the speaker icon in the tray, and raise PCM and Front to maximum.

---

### Post by StOoZ on 2008-08-14
maybe its muted? (check the speaker icon on the lower right...)
if no , in terminal type :
> lshw -C sound

and pate it here

---

### Post by kelvinlokahong on 2008-08-14
Thx everybody. Unfortunately I didn't work.
I typed in lshw -C sound and it comes out as:
" *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

