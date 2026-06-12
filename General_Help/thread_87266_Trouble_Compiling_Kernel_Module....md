---
title: "Trouble Compiling Kernel Module..."
date: 2005-11-07
forum: General Help
---

### Post by ElricOfGrans on 2005-11-07
G'Day,

I am experiencing a strange problem with recompiling a kernel module. I last compiled a month ago, and in that time the module source, kernel version and (crosscompiler) toolchain all remain unchanged: all that has changed is that I have upgraded to Breezy (hence all other utilities have been updated).  Because all of the aspects which should directly impact this are unchanged, I am at a loss to explain why it no longer works.

My problem is this: when I compile my module, everything starts as normal, and it compiles, like so...

```
$ make
make -C /usr/src/linux/ M=/home/matthew/src/c/modules/omap-owire-dev modules
make[1]: Entering directory `/usr/src/arm-linux-2.6.13-rc4'
  CC [M]  /home/matthew/src/c/modules/omap-owire-dev/omap_owire.o
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/arm-linux-2.6.13-rc4'
```

This is where it ends: for some reason it does not perform the linking process, and as such the omap_owire.ko file is never created; omap_owire.o, .omap_owire.o.cmd, and .tmp_versions/omap_owire.mod are all created.

I am able to recompile the kernel itself without any difficulties, as I can with regular applications, so I cannot explain this one. Any suggestions would be most appreciated!

---

