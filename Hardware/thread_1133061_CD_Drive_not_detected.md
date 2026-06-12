---
title: "CD Drive not detected"
date: 2009-04-22
forum: Hardware
---

### Post by SuperSonic4 on 2009-04-22
This has been puzzling me for a while now so I thought I'd make a topic on it :KS

My (secondary) dvd writer is not being recognised whenever I put a disk in (whether it is a cd, dvd, or writeable optical media) it seems to whir but neither vlc nor dolphin can open the contents

Running vlc from a terminal gives: ```
[00000406] dvdread demux error: DVDRead cannot open source: /dev/sr0
[00000409] main access error: no access module matched "dvd"
[00000405] main input error: open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd"

```

It does not work in windows either but the BIOS picks it up at boot and recognises that it is in sATA channel 1. The model is **Optiarc AD 7200-S** and it is on firmware 1.0A

[Model](http://www.ebuyer.com/product/139414)

---

### Post by GOROSSI on 2009-04-22
Have you Tried booting a Live CD 
Or Tried in another machine? 

If you have done those and still don't work it's most likely gone to drive heaven. 

If there such a place it would probably be too full of Floppy drive's to fit anything else in lol.

---

