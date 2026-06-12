---
title: "Japanese directory names through samba"
date: 2008-07-21
forum: General Help
---

### Post by wimmelis on 2008-07-21
Dear All,


Currently, I connect to a few windows servers through samba, but some of these servers have directories with japanse names, so I only see ???? or so. I have japanese character set installed on my ubuntu, but have not yet managed to figure out how I can watch the contents of these folders. Anyone any ideas ?


Thanks

WM

---

### Post by wimmelis on 2008-08-04
Dear all, 


For completeness to whoever searches this forum.
The solution is simple, it is better to mount your drives as cifs than as smbfs, and then you simply add the option iocharset=utf8.


Good luck,

WM

---

