---
title: "nVidia Driver Issues"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by OlineSixtyOne on 2005-12-26
I installed the nVidia driver for my 6600GT PCI-E via Automatix. I set custom gamma and vibrance settings, but whenever I start up and login they do not apply the settings. If I go to Applications -> System Tools -> nVidia Settings, the settings dialog opens and the gamma and vibrance setting are instantly applied. It's a pain to do this every time I start the system, is there any way to fix it?

---

### Post by OlineSixtyOne on 2005-12-28
ummm bump

---

### Post by OlineSixtyOne on 2005-12-29
bump again.

---

### Post by OlineSixtyOne on 2006-01-05
Bump. This is getting absurd, someone please help.

---

### Post by OlineSixtyOne on 2006-01-07
Help Me!!!!!

---

### Post by mo_x on 2006-01-07
You have to run:
nvidia-settings --load-config-only
when you start the X server. See the nvidia-settings manual page.

---

### Post by OlineSixtyOne on 2006-01-08
Thanks, worked for me.

---

