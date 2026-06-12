---
title: "Recovering data on an external drive with photorec"
date: 2010-05-06
forum: Hardware
---

### Post by Struki on 2010-05-06
I messed up, doesn't matter why, I was just wondering...
I'm recovering data on a 120 gigabyte external hard, connected via usb, and photorec displays around 100hrs until the files are restored. Since this is my first time I'm wondering, is this normal?

---

### Post by mennowo on 2010-05-06
Photorec will basically read the entire disk, even if the index says there is no file, from beginning to end. Anywhere where Photorec reads actual data, either as a complete file or a part of a file, it will write this data to the appointed place.

So, yes, for 120 gigs this may take a very long time. I've done this a while back for a 2 gig memory card, and it took like 20 or 30 minutes...

Goodluck!

---

