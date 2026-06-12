---
title: "intel 950 chipset, xorg.conf, i915, unity... help!"
date: 2011-07-04
forum: Hardware
---

### Post by ubunwhat on 2011-07-04
I keep getting closer and closer to a solution here, but I'm just not finding it.  I'm not even sure if I'm posting questions in the right forum.  So here is my issue.  I have a Toshiba Satellite with the gma 945 / 950 chipset.  The only way that I can get into Ubuntu is with nomodeset.  Everything else that I have tried just gives me a black screen after the Grub.  The problem is that Unity does not work with nomodeset so I am relegated to classic mode.  I would love to find a way to get into Unity with this machine, which means some solution other than nomodeset.  I have found a few solutions but I don't think that I am well versed enough in Linux to pull them off.  

One solution talks about editing the xorg.conf file to enable xma, but I'm not finding an xorg.conf file on this machine and am reluctant to start creating configuration files blindly.  The thread with that solution is over two years old and pertained to Jaunty, so I'm not sure if that is even applicable to 11.04.

The following is the result of my Unity support test, if that helps

```
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.12-devel

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
```

I've tried to get around nomodeset by using i915 mode=0 xforceversa, but that just left me with the black screen.  There has to be some way to make this thing work.  Any ideas?

---

