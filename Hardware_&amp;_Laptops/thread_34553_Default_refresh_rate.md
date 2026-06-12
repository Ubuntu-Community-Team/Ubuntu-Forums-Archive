---
title: "Default refresh rate?"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by Julius on 2005-05-15
I've got a new monitor and it works better with 1280x1024@60Hz. It doesnt look that bad with 75Hz, but it's not as sharp as 60. 

Anyway, xorg by default will use 75Hz, so GDM will always be using that refresh rate. As a result the screen is kinda moved to the left. Any changes I make within my session will not be system-wide.

I've been trying to understand how xorg.conf handles this configuration, but I just can't. THe only thing I know is this:

FH = 65 kHz
FV = 60 Hz

(according to my monitor manual).


ANy suggestions?

---

