---
title: "PAE in 8.10 desktop?"
date: 2008-10-24
forum: General Help
---

### Post by ErroneousBosch on 2008-10-24
Does anyone know if Ubuntu will do the smart thing and include PAE in the 8.10 generic kernel? It's really frustrating to have 4 gigs of ram and not be able to use it all, especially in GIMP.

---

### Post by jerome1232 on 2008-10-24
Why not install the server kernel? It has PAE enabled, or better yet if your processor supports it install 64-bit, no pae required for that ram.

it's as  simple as
```
sudo apt-get install linux-server
```

---

### Post by aurelieng on 2008-10-24
The server kernel has been compiled with PAE (which solves the problem) and with Xen related things. The latter prevents the installation and use of the NVidia proprietary drivers. Depending on your configuration, this may create another problem, which can be solved by compiling your own kernel, with PAE but without Xen support. Such a kernel in the official repos would be great, as most users do not want to recompile things, and do not want to choose between 4Gb of RAM and graphical hardware acceleration.

---

### Post by jerome1232 on 2008-10-24
I didn't realize that about the server kernel, I guess it would be nice for those stuck in 32bit land.

---

### Post by aurelieng on 2008-10-24
We can discuss it there : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224340](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224340)

---

### Post by sdennie on 2008-10-24
The server kernel does prevent the compilation of the nvidia drivers but, if I'm not mistaken, if you are currently using the vanilla nvidia-glx-new packages (so, you haven't downloaded and manually installed the nvidia drivers), you can install the server kernel in the following way and you will maintian graphics acceleration:

```

sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server

```

You could probably turn off the Xen checks in the manually installed driver and do the same but, I've not looked into that.

Also, see this thread about Ubuntu with 4GB of RAM: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by aurelieng on 2008-10-29
> **vor said:**
>  ... you can install the server kernel in the following way and you will maintian graphics acceleration ...
Well, it does not work, at least not for me.

---

