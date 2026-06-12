---
title: "USB 16 gig  usb"
date: 2016-12-24
forum: Hardware
---

### Post by pete1977x on 2016-12-24
I formatted my Sandisk 16 gig USB drive with ubuntu format  on the Disk utility thing. When I put in the usb it shows as 2 devices..one has 15 gig and the other shows 105 mb.
What is up with this?? I am putting music on it for a car` stereo that plays from USB stick.

---

### Post by mikewhatever on 2016-12-25
You've likely chosen GPT partition scheme, which is unlikely to work in a car. Make sure you select FAT as file system, and MBR instead of GPT, if required.

---

