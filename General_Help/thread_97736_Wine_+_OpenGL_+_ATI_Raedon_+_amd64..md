---
title: "Wine + OpenGL + ATI Raedon + amd64."
date: 2005-12-01
forum: General Help
---

### Post by fakeh on 2005-12-01
I'm trying to play WoW and have encountered a (seemingly) common problem but with a (seemingly) uncommon cause.

I get lots of 

```
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!

```

happening just as described in [http://www2.ati.com/drivers/linux/linux_3.14.6.html#174635]("http://www2.ati.com/drivers/linux/linux_3.14.6.html#174635")

however, I already have /dev/shm mounted.

My situation: running amd64 with a 386 chroot with wine installed from CVS (with a patch applied and OpenGL compiled in).

Many thanks for any ideas anyone has.

Dan.

---

### Post by teaker1s on 2005-12-01
not suggesting it is but try altering the windows version wine uses with 'winecfg' and see if it works I found nt4.0 better choice than xp in many situations

---

### Post by fakeh on 2005-12-01
I've tried several versions now, all with the same results.

Dan.

---

### Post by fakeh on 2005-12-01
I was stupid, delete this thread please.

Dan.

---

