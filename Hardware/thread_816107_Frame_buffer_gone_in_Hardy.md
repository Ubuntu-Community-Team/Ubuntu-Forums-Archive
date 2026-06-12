---
title: "Frame buffer gone in Hardy?"
date: 2008-06-02
forum: Hardware
---

### Post by randysparks on 2008-06-02
It seems there's no longer a /dev/fb0 in Hardy. Has the frame buffer been deactivated? Is there any way of reactivating it?

---

### Post by randysparks on 2008-06-02
Hmmm... there's a file: /etc/modprobe.d/blacklist-framebuffer and it begins with the comment line:

*Framebuffer drivers are generally buggy and poorly-supported, and cause suspend failures, kernel panics and general mayhem. For this reason we never load them automatically. *

Is this the reason why there's no framebuffer device?

---

