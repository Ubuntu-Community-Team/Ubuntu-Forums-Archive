---
title: "Hardy+nvidia: undefined symbol: _nv000043gl"
date: 2008-04-30
forum: Hardware
---

### Post by vexorian on 2008-04-30
I must really ask, has any hardy user out there accomplished to make nvidia-glx-new actually work, without using things such as envy or the driver from nvidia's site? Cause I get this in my Xorg.0.log:

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000043gl
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

I check both libGLcore.so.1 and libglx.so and it all looks like they are those installed by nvidia-glx-new, so this is not a conflict, it almost looks like one of those files in the package is just wrong from the very source (repository).

So, if anyone got nvidia-glx.new working in hardy without problems I'd really like to know. It would also be a happy thing to be able to have 3d acceleration in ubuntu again , it would be quite hard to me to stand not being able to play warcraft III or gta for long because of this :) Everything else works (not without work from my part) resolution, drives, etc.

PS: If you got a solution to get nvidia 3d acceleration work in hardy, please don't post it if it includes using envy or a driver from nvidia's site, I had too many bad experiences with those in the past.

---

### Post by PauGNU on 2008-05-01
Maybe this will solve your problem?
[http://ubuntuforums.org/showthread.php?t=378982](http://ubuntuforums.org/showthread.php?t=378982)

---

### Post by vexorian on 2008-05-01
I did find that one, but there are issues:

* gl-mesa is requisite to like 100 packages, so  I can't remove it easily, reinstalling does not fix it.
* I do not understand -Nabla-'s post.
* It looks like it is not the same problem cause both of my .so files do seem to point to the 169 driver in glx-new.

Edit: I gave up and installed a nvidia driver 169 (from the site) I had around in my hard drive, it works. It'll be annoying to have to recompile it every time I update the kernel but it looks like it is the only way...

---

