---
title: "Custom ramdisk?"
date: 2009-08-25
forum: Hardware
---

### Post by fela on 2009-08-25
I'd like to make a custom ramdisk, put it in the fstab, and mount it at boot. Is this possible? Actually, how do you do it? I know it's possible :)

Also, once I have that going I'd like to preload applications like firefox libs, etc. to it to make them run super fast on startup. This is a different problem to solve, but I think the ramdisk should be about 128MB in size. I could also use it for my temporary files dir if I can change firefox's one (as I download large files alot).

So, how would I go about all this then? Thanks :)

UPDATE: I just tried ramfs, but for some reason it reports 0bytes available...strange. It seems to be a relatively common problem.

---

### Post by andrewabc on 2009-11-07
Found your post via forum search.

To load some files into ram at startup install program called
preload
found in synaptic. It has algorithms and stuff to figure out what most used programs/libraries are used and to put them in ram.
I'm currently having problems with it in 9.10, but it worked fine in 9.04.

---

