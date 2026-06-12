---
title: "Touchscreen almost working - what next 12.04?"
date: 2012-05-18
forum: Hardware
---

### Post by deport on 2012-05-18
Ubuntu 12.04

The touchscreen does not completely function.   The regular mouse moves the cursor fine.  On some level Ubuntu sees the touchscreen, and I can view a character rendition of the digital data.

sudo cat /dev/ttyS4
   and touching the screen gives me random characters, so some data is flowing, but not as a mouse.

This also works for /dev/input/input4, /dev/input/mouse1 and /dev/input/mice
When using /dev/input/mice than both my regular mouse and the touchscreen put out the characters.

i use serialattach in the rc.local file

xinput shows   Elo Serial Touchscreen at ID 10

**How do I finish configuring ubuntu for this device?**

---

