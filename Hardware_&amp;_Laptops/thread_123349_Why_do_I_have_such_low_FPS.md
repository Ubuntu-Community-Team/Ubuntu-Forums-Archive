---
title: "Why do I have such low FPS?"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by grit on 2006-01-29
GLXGears:

81 frames in 5.0 seconds = 16.157 FPS
154 frames in 5.1 seconds = 30.461 FPS
148 frames in 5.0 seconds = 29.487 FPS
121 frames in 5.0 seconds = 24.120 FPS
163 frames in 5.0 seconds = 32.280 FPS
132 frames in 5.0 seconds = 26.219 FPS
127 frames in 5.1 seconds = 25.088 FPS
152 frames in 5.0 seconds = 30.259 FPS
120 frames in 5.0 seconds = 23.946 FPS
121 frames in 5.0 seconds = 24.167 FPS
156 frames in 5.0 seconds = 31.097 FPS

As far as I can tell everything is configured correctly...

[http://www.zen46671.zen.co.uk/Xorg.0.log](http://www.zen46671.zen.co.uk/Xorg.0.log)
[http://www.zen46671.zen.co.uk/glxinfo.txt](http://www.zen46671.zen.co.uk/glxinfo.txt)
[http://www.zen46671.zen.co.uk/xorg.conf](http://www.zen46671.zen.co.uk/xorg.conf)

Really unsure what the problem could be :confused: Please help me, I miss my gaming!

---

### Post by Schotty on 2006-01-29
I cant say for certain, but one thing is to kill dri support.  nVIDIA doesnt need it, as its already in their kernel module.  Just comment out the references in the xorg.conf (two sections, the include and then the parameter section at the end).

---

### Post by grit on 2006-01-30
[QUOTE=Schotty]I cant say for certain, but one thing is to kill dri support.  nVIDIA doesnt need it, as its already in their kernel module.  Just comment out the references in the xorg.conf (two sections, the include and then the parameter section at the end).[/QUOTE]

Ok will do thanks.

---

