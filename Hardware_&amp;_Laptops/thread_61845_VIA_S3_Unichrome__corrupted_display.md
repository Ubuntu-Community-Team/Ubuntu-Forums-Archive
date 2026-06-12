---
title: "VIA S3 Unichrome : corrupted display"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by alci on 2005-09-02
Hi,

I have just installed Hoary, on a computer with "VIA Technologies, Inc VT8378 [S3 UniChrome] Integrated Video (rev01)" (this is lspci utput).

Installation went smooth, except the display is "corrupted". Lines are like interlaced, like on a crypted TV program... Quite unreadable.

In xorg.conf, driver is "via".
I tried to add Option "NoAccel" but it doesn't change anything...

Any tip ?

Thanks,
Franck

---

### Post by undeadsoldier on 2005-09-02
Nobody else bothers to answer questions...

Try using vesa instead of via in your xorg.conf file

---

### Post by alci on 2005-09-04
Thanks,

vesa driver works. I had to tweak the screen resolutions (was 600x400) and everything is fine.

Thanks a lot for the answer,

Franck

---

### Post by scabies on 2005-10-26
modifying /etc/X11/xorg.conf to use "vesa" instead of "via" also solved this problem for me.

(i'm on breezy 5.10, btw).

---

