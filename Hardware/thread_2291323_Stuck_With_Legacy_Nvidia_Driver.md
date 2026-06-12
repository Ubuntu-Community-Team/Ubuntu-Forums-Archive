---
title: "Stuck With Legacy Nvidia Driver"
date: 2015-08-19
forum: Hardware
---

### Post by jim_deadlock on 2015-08-19
I'm trying to change to a newer driver for my Nvidia card but it seems to be stuck on the legacy driver. I tried selecting other drivers, the progress bar moves but then it stays on 304.125. Is this because my card is too old for the newer drivers?

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/nvidia_1.png[/IMG]

---

### Post by dino99 on 2015-08-19
your card is not too old :o it support the latest 355 driver

so go for a nvidia*purge, then install nvidia-352 or up (xorg-edgers ppa)

---

### Post by jim_deadlock on 2015-08-19
That did the trick, thanks! I think nvidia-persistenced was missing.

---

