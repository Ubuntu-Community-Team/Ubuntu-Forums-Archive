---
title: "Wubi Questions."
date: 2008-10-16
forum: General Help
---

### Post by Cue89 on 2008-10-16
Dear,

I am new to Ubuntu and i wan't to try it with Wubi, i have done some research but i still have some questions:

1. Does the behavior of the Windows operating system affect Ubuntu?
2. Can you install packages?
3. Can you save settings/changes?

Thanks in advance,

---

### Post by ago on 2008-10-16
> **Cue89 said:**
> 
1. Does the behavior of the Windows operating system affect Ubuntu?
Only at file-system level: if the file-system is fragmented, Ubuntu will slow down, and if the filesystem is corrupted, you will not be able to boot into Ubuntu at all until you fix that (chkdsk) 

> 2. Can you install packages?

Yes, you can do anything you could do in a normal installation other than hibernate

> 3. Can you save settings/changes?
Yes

---

### Post by Cue89 on 2008-10-16
Oke thanks, is it also slower because it doesn't have a swap partition?

---

### Post by ago on 2008-10-16
> **Cue89 said:**
> Oke thanks, is it also slower because it doesn't have a swap partition?

It does have a swap "partition", or better it's a swap file. Particularly in 8.10, writes to swap will be a bit slow. 

With today's memory, you shouldn't see very high swap usage anyway.

---

