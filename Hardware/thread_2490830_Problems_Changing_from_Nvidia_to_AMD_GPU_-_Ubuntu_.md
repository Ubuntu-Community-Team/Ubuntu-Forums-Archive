---
title: "Problems Changing from Nvidia to AMD GPU - Ubuntu 23.04."
date: 2023-09-17
forum: Hardware
---

### Post by joaocrespo on 2023-09-17
Hello world.

I just replaced my Nvidia GTX 1070 with an Amd 7700.

Originally video resolution was OK (but showed 0 HZ as refresh rate) and sound stop working with the switched, then I run the pending updates and the sound is still not working and video resolution is now also screwed  (is running 1024 x 768 at 76hz, native is 1920x1080 at 144hz).

My suspicion is that the Nvidia blobs "tainted" either the kernel or xorg (or both), causing this issues.

Any ideas?

Thanks in advance.

---

### Post by deadflowr on 2023-09-17
Did you remove any xorg.conf files that would have been generated when setting up the nvidia drivers?
Did you remove the nvidia drivers?

Other then switching one card for another it's not clear what has or has not been done so far.

---

