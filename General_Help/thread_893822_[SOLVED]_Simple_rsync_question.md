---
title: "[SOLVED] Simple rsync question"
date: 2008-08-18
forum: General Help
---

### Post by geo909 on 2008-08-18
Hello everybody,

I remember there was a flag when using rsync to synchronize folders, that
made rsync not affecting files that were modified later on the destination folder..

Do you have an idea which was that?

Thanks in advance!

---

### Post by RealPSL on 2008-08-18
From the man pages:
>        **-u, --update**
              This  forces rsync to skip any files which exist on the destina&#8208;
              tion and have a modified time that  is  newer  than  the  source
              file.   (If an existing destination file has a modify time equal
              to the source file’s, it will be updated if the sizes  are  dif&#8208;
              ferent.)


---

### Post by geo909 on 2008-08-19
Thanks!

---

