---
title: "3D intel graphics"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by spotslayer on 2006-12-19
I have googled extensively and posted this question on several forums. I have seen responses from every extreme. I have seen I am using the same driver and don't see that to the obvious, I have the same problem. I have been told it is a Mesa problem, it is a driver problem, it is no problem. It is true everything works, but my glxgear numbers are in the 1003-1007 range. My graphics are slow. My search has not led me to any solution. Can anyone shed some real light on this issue.

**libGL warning: 3D driver claims to not support visual 0x5b**

GL_RENDERER   = Mesa DRI Intel(R) 945GM 20050225
GL_VERSION    = 1.3 Mesa 6.5.1
GL_VENDOR     = Tungsten Graphics, Inc


David

---

### Post by zgornel on 2006-12-19
There is no light to shed. That's as good as it gets. I've been looking for solutions too but at this point there aren't any. My glxgears framerate is about 980fps.

---

### Post by Bagnaj97 on 2006-12-19
I get the same error reported but I still have 3d acceleration. Compiz runs as does Quake3. I'm not sure if it should be even faster 3d acceleration though. What exactly do you mean when you say your graphics are slow?

---

### Post by DarkN00b on 2006-12-19
I get the same error except it is 0x4b instead of 0x5b. My glxgears fps score was 491 fps, then after I started Beryl, it jumped up to 524 fps for some reason. My system is perfectly fine at this fps. You should judge your system by how it actually runs instead of using artificial benchmarks like glxgears.

As far as I know, there is nothing that can be done about the error.

---

### Post by spotslayer on 2006-12-19
Well the reality is I have already decided that there was nothing to be done at this time. I was just wondering what the problem was. There may be fixes in the future and I just wanted to know which area to watch for the solution. 

By slow I mean the graphics don't pop the way they do in windows. My friend has the same setup I do only he is a windows person and his graphics have a snap that mine don't. 

David

---

### Post by zgornel on 2006-12-20
I agree. For example, a simple timedemo in Quake 3(1024x768, all options at max quality) shows 25fps in Edgy (with wine, cedega and native binaries) and ~100fps in Windows. It bugs me especially because there are so many laptops with intel integrated graphics and support is to say at most poor.

---

