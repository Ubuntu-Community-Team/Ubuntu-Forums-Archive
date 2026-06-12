---
title: "Tv-out with Intel 82830?"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by Aninhumer on 2007-01-14
I have installed the ubuntu server version on an old laptop (as it has only ~128mb of memory and none of the graphical versions would load) with intent to use it as a mythtv frontend.

I have mythtv setup, and it works fine with an external monitor (The internal monitor has a faulty connection) but I need to get it to work with my TV.
As the laptop has an S-Video port, I have been trying to get this to work.

On an [old mailing list]("http://www.vobcopy.org/pipermail/r31/2004-November/000547.html") I found instructions to add this to my xorg.conf, Device section:
```
Option          "MonitorLayout" "TV"
```

Adding this line appears to get an S-Video output, but the output is not at the correct resolution (or something similar, only strange scan lines appear).

I have set the device driver to i810, as I believe this is correct for my hardware.
What else do I need to do to get the correct output? 

PS: If there is no way to get a usable output with the S-Video, is there any other way to get tv-out?

---

### Post by Aninhumer on 2007-01-14
Here is my lspci output, and my xorg.conf file.

---

### Post by Aninhumer on 2007-01-14
Please help me.

---

### Post by Aninhumer on 2007-01-15
:(

---

