---
title: "Investigate suspend problems"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by chilly_willy2 on 2007-12-09
Hello all,
I'm using Ubuntu 7.10 on a Thinkpad R50e and am having problems waking up from suspend-to-ram and suspend-to-disk. With all previous Ubuntu versions (minus 7.04, which I never tested), suspend-to-ram never worked but suspend-to-disk ALWAYS worked. It was great!

Now, my lappy goes to sleep either way just fine. However, upon waking up, I get the following results:

*suspend-to-ram: black screen with mouse cursor; nothing can be clicked; I can switch to console (CTRL-ALT-F#) and reboot. Then all is well.

*suspend-to-disk: mouse cursor appears and is movable; the only part of the screen which is not black is a ~30x30 pixel square that surrounds the spot the cursor appeared when it woke up. I cannot switch to another console. My only option is to hard-reset.

I did try one thing: change my video driver from "intel" to "vesa" and restarted X. That produced weird -- not better -- results.

Any ideas? What should I be investigating? Thanks!
-Chris

---

