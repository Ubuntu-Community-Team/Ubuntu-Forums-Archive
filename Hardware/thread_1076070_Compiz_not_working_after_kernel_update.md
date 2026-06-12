---
title: "Compiz not working after kernel update"
date: 2009-02-20
forum: Hardware
---

### Post by biehlbuddy on 2009-02-20
There was a kernel update for 8.10 a few weeks ago and after it Compiz stops working.

Video card:
Radeon Mobility M6 LY

compiz --replace output:
```

matt@matt-laptop:~$ compiz --replace &
Checking for Xgl: [3] 6129
matt@matt-laptop:~$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```

Thoughts anyone?

---

