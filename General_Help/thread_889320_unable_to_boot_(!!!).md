---
title: "unable to boot (!!!)"
date: 2008-08-14
forum: General Help
---

### Post by K_REY_C on 2008-08-14
Hey all:

Okay... so I've been using ubuntu for about 3 months now but I totally messed up my system doing something.

I've been running the WUBI install.

Here's what I'm getting when I try to boot up:

Booting 'Ubuntu 8.04.1, kernel 2.6.24-19-server'

Filesystem type is ntfs, partition type 0x7
[Linux-bzImage, setup=0x2a00, size=0x1e2598]
[Linux-initrd @ 0x1f8d4000, 0x71b254 bytes]
This kernel requires the following features not present on the CPU:
0:6
Unable to boot - please use a kernel appropriate for your CPU

Any help appreciated. I must have mucked something up but I'd really like to get it fixed if possible. 

Thanks!

KYLE

[I've used "recovery mode" and it has booted up... but do I need to do anything to ensure it will boot up normally in the future?]

---

### Post by K_REY_C on 2008-08-14
Solved my own problem - much later though. 

Here's what was going on with me:

When I went into the boot options ('esc' before boot) I saw that there were 3 kernels installed - the top one being the server kernel. 

I needed to boot into a non-server kernel, go to synaptic package manager, search for 'linux-image', and uninstall the server kernel.

All problems went away. Ubuntu boots on it's own with no additional keystrokes for me. 

Hope this helps someone else.

KYLE

---

