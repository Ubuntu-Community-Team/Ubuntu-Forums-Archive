---
title: "Netbook Suspends Immediately on Battery"
date: 2009-11-15
forum: Hardware
---

### Post by mooreted on 2009-11-15
Using UNR 9.10 on an Acer Aspire One. On Windows or Puppy Linux, I can pull the AC jack and run on battery power for a long time. Wind UNR my netbook suspends immediately when I pull the AC jack. I have set the power settings to never suspend even on battery power, but it still does it.

---

### Post by mooreted on 2009-11-15
After reading a bug report, it looks like it's a problem with HAL or possible the kernel. Removing the AC jack triggers a lid-close state so the netbook suspends. I changed the power options to blank screen on lid-close and I can run on battery now. I guess I will have to suspend manually until the bug is fixed unless someone has another solution.

---

