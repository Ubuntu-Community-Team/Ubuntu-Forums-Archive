---
title: "hard drive input/output error"
date: 2008-11-15
forum: Hardware
---

### Post by carboncopied on 2008-11-15
it seems I have left my computer on while someone plays with the circuit breaker one too many times.

when I open my large partition on my storage drive (no back up, yes I know it's stupid) I can longer see the folders that should be there. I cannot make a folder either. it comes up with an input/output error. 

[In windows the computer says it needs to be reformatted. I run hardy heron.]

The files are still there. If I know the folder name, I can open up the folder and use the files as if nothing was wrong. 

I tried running  sudo e2fsck -b 8193 /dev/sdb5

and it comes back saying 

e2fsck: Device or resource busy while trying to open /dev/sdb5
Filesystem mounted or opened exclusively by another program?

I read that the problem is involved with the block layer device, but haven't found how to fix it.

Any help would be greatly appreciated. Thanks.

---

