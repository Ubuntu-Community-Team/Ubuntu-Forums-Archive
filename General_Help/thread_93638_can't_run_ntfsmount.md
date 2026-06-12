---
title: "can't run ntfsmount"
date: 2005-11-22
forum: General Help
---

### Post by M-Theory on 2005-11-22
hi,

I just installed ntfsprogs 1.12.1 from source in breezy. I would like to use ntfsmount to mount a ntfs volume with FUSE. Unfortunately I get this error when trying to run ntfsmount: "bash: ntfsmount: command not found".
I'm sure ntfsprogs installed correctly because "ntfsinfo -V" returns version 1.12.1. Does anyone have any ideas about why I can't use ntfsmount? Thanks!

---

### Post by aysiu on 2005-11-22
Are you sure that's the right command for ntfsprogs?
Did you know you can install that program from Synaptic/apt-get (you didn't have to do it from source)?

Is mounting NTFS partitions all it does? If so, you don't need that program.

---

### Post by M-Theory on 2005-11-22
the repository has an old version (1.9.4-2) and I don't think that version supports ntfsmount at all. Besides, I already tried it with that version without success.
I want to use it to be able to write to a ntfs partition, it's still experimental but safe compared to the kernel ntfs driver if I understand correctly.

---

### Post by M-Theory on 2005-11-22
problem solved... I had to install libfuse-dev before installing ntfsprogs.

---

