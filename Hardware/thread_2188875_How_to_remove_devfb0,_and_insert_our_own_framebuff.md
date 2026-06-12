---
title: "How to remove /dev/fb0, and insert our own framebuffer driver creating fb0"
date: 2013-11-19
forum: Hardware
---

### Post by akashhajari on 2013-11-19
I want to remove system's existing fb0, so that I can test my fb driver, for display driver understanding purpose.
I am using Ubuntu 12.04 (64 bit) on x86 m/c. I already created /dev/fb1 using vesafb.
But now, I want to remove fb0 and it's intel frame-buffer driver. So that I can insert my frame buffer driver, which will create fb0.

So, please suggest me how to remove /dev/fb0 and Intel's frame buffer driver, so that I can insert my custom framebuffer driver.

Thanks,
Akash Hajari.

---

