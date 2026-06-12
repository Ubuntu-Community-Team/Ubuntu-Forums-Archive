---
title: "No suspend in 2.6.33 mainline kernel on old machine"
date: 2010-03-28
forum: Hardware
---

### Post by dda on 2010-03-28
I'm running Ubuntu 9.04 on some old desktop (P-III 533MGz), and some time ago installed kernel 2.6.29 from mainline, it was working fine. Recently I added 2.6.33 from mainline, and noticed two things:

- the system can not be suspended anymore (only hibernate is available in menu)
- text consoles (vt1-vt6) are blank (framebuffer problem?)

Booting back in 2.6.29 solves both problems. I wonder, if it can be corrected by passing some parameters to the new kernel, or it is a regression which can not be fixed. I'm attaching dmesg output from both kernels, what else can I add to the post to help solving it?

dmesg with 2.6.29 kernel: [http://paste.org/pastebin/view/16792](http://paste.org/pastebin/view/16792)
dmesg with 2.6.33 kernel: [http://paste.org/pastebin/view/16793](http://paste.org/pastebin/view/16793)

Best regards,
Dmitry.

---

### Post by dda on 2010-04-02
Did I post to a wrong forum?

---

