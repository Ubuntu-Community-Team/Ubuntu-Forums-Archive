---
title: "Boot failure."
date: 2008-12-01
forum: General Help
---

### Post by phaedrus85 on 2008-12-01
I am using 8.10, and earlier today I updated all my repositories; including the kernel, which is where I believe I'm having problems. The UI will not load at all after my update and restart. When I attempt to boot, at the ubuntu logo screen with the UI loading bar about halfway, the loading sequence moves immediately to a shell/grub loading screen, with a series of errors.

To summarize, the boot failed and gave this message "*Unexpected inconsistencies; run fsck manually"

It reads that the file system check failed, then that it should be in read-only mode. Whereupon it reads that it is already in read-only mode, but it still failed, leaving me with exit status 4.

The last bits are a series of "bash:" with the following after each:
no job in this shell
lesspipe
command
the
dircolors
command
the

The result for each of those was "command not found"

I'm not sure what happened, or how to correct it, and my knowledge of Ubuntu is somewhat limited. Never encountered this before. Should I correct this somehow using a LiveCD? Anything I can do from the shell before the UI boots?

Any insight is appreciated.

---

