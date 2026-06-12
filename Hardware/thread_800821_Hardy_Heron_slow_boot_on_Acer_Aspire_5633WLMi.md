---
title: "Hardy Heron slow boot on Acer Aspire 5633WLMi"
date: 2008-05-20
forum: Hardware
---

### Post by stoodleysnow on 2008-05-20
I installed Hardy afresh on my Acer Aspire 5633WLMi laptop shortly after the release day. I have kept it up to date with the latest updates, but it seems to be booting a lot slower than it did with Gutsy.
Spec:
Intel Core 2 Duo 1.66GHz
1GB RAM (2x512MB)
120GB HDD of which about a third is used
DVDRW drive (slim)
1440x900 max res screen.

It always seems to get stuck at about 18% of the bar, and waits for ages before finally moving on to complete the boot. This problem repeats every time I boot the laptop.
It does not seem to happen with my slightly higher spec desktop.
Ideas? :confused:

---

### Post by doobydave on 2008-05-20
Edit the grub boot line to remove the words "quiet splash" from the end. This can be done at the grub menu by highlight the appropriate entry and pressing 'e' (for edit) -twice.

once deleted, press 'enter' and then 'b' for boot.

This should provide some leads.

My guess it that it could be the webcam, but check with above method.

---

