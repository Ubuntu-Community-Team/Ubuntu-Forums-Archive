---
title: "GL vertex buffer object problem"
date: 2011-04-29
forum: Hardware
---

### Post by t36 on 2011-04-29
Hi,

I just updated to the latest version of Ubuntu 11.04 and I wanted to try out the Unity interface. However, I get the message that my hardware does not support Unity.

I ran ```
/usr/lib/nux/unity_support_test -p 
``` as was suggested in the wiki

and got this output

```
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series 
OpenGL version string:  1.4 (2.1 (4.1.10665 Compatibility Profile Context))

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

Is there any way I can fix this? Or does my video card not support this GL vertex buffer object.

Thanks in advance,

t36

---

### Post by PhoneixS on 2011-10-17
I have the same problem. Someone know something about it?

---

### Post by vinterkind on 2011-12-21
I had the same problem. I solved the problem (not satisfying enough for me, but it worked) as followed:

**1. I removed (purged) all ati-based drivers**

You may check on your installed ones with 

```
dpkg -l | grep fgl
```And purge them like 

```
apt-get remove --purge fglrx fglrx-amdcccle 
```Testing the default systems driver for ati/radeon afterwards I had an X-Server crash when invoking 

```
/usr/lib/nux/unity_support_test -p
```and my dash-bar vanished ...

**2. I reinstalled unity** (I guess that's not really necessary, you may try without it)

**3. I downloaded and installed the prop. ATI driver 8.881**

and since the driver doesn't seem to work (The X-Server couldn't start), 

**4. I installed the systems fglrx driver** (again)

Luckily enough for me, it worked. (After several *service gdm* *stop*'n *start*s) :-)

---

### Post by gryspnik on 2012-07-26
Can you please elaborate on how you did that?
CHeers

---

