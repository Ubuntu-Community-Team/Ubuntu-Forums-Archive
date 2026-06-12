---
title: "How to get external HDMI monitors recognized."
date: 2020-07-16
forum: Hardware
---

### Post by guleblanc on 2020-07-16
So this is not a question, it's an answer to an unasked question. It's been asked, without real good answers before, but all the threads have been locked. Since I struggled with this for a long time, most recently the past few days, I thought I would answer it proactively.

I have an older, ViewSonic LED monitor which I wanted to connect to my newer Lenovo laptop. The laptop would recognize the monitor fitfully, maybe one in twenty times I booted it up. I did all the things I found in forum comments - changing to gdm3, changing back to lightdm, changing from the nVidia driver to the nouveau driver and back again and some other stuff none of which worked. I finally went into the UEFI setup, which is probably the same as the BIOS setup on older machines, and found a display parameter called BOOT EXTENSION. Apparently you can set the boot to extend the boot time by several seconds to allow older monitors to boot up. I set it from no extension to 3 seconds, and my monitor is now being recognized reliably at every boot.

So, if you are having trouble getting your older monitor to be recognized, try the BIOS settings.

---

