---
title: "Samsung SPF-85H"
date: 2009-06-19
forum: Hardware
---

### Post by rmccarri on 2009-06-19
Hi,
My wife got me a Samsung SPF-85H photo frame as a present.  It's a great little frame, but unfortunately, I have been unable to mount the 1 GB internal storage.  Has anyone been able to successfully mount a digital photo frame in Ubuntu?  I'm kinda surprised that it doesn't work.

** UPDATE **

Apparently there was a problem with the fstab or something.  I rebooted with the frame plugged in and it was mounted properly.

---

### Post by salil on 2009-06-27
I had the same problem. I tried rebooting with the frame plugged in, but still it wouldn't automount.

Found this bug report: 
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/334308](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/334308)

I was able to manually mount it, in the same manner as described in the above link. Then I tried the workaround mentioned by Frodon (comment 6) in the above link, that is, formatting the frame to FAT32, and now everything works fine (transferring photos).

-Salil.

---

