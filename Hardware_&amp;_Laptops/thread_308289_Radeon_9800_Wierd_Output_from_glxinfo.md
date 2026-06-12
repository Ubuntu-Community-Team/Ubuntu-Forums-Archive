---
title: "Radeon 9800: Wierd Output from glxinfo"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by Tarvok on 2006-11-27
I'm trying to get Cedega up and running, and my comp failed both the direct rendering and 3d acceleration tests, so I thought I'd check out the docs on getting 3d acceleration working. I started with step 1:

> tarvok@rider:~$ glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
direct rendering: Yes

Okay, so I got direct rendering: Yes. What's all that other stuff?

BTW, I'm running the AMD64 kernel (AMD Sempron 64 2800), have a Radeon 9800, under Dapper Drake (6.06 LTS). Any idea what's wrong here?

Oh, and if you can help me with another thing, Cedega failed the ALSA test, too (though OSS works).

---

### Post by burwaco on 2006-11-28
I heva the same error scince I upgraded from Dapper to Edgy. Not as many as you ...

root@box:/# glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

I read somewhere in the wiki that there is another driver for ATI in Edgy, maybe that solves the problem.
For the moment ET is running fine here, so it doesn't bother me.

---

