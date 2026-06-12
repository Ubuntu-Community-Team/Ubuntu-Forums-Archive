---
title: "rsync include/exclude"
date: 2008-07-18
forum: General Help
---

### Post by walmartshopper67 on 2008-07-18
ive got a Quick question: with rsync can you copy files outside of the main path specified on the command line? i tried putting the outside directories in my include/exclude files but it never includes them.

---

### Post by kpkeerthi on 2008-07-18
No you can't. 

rsync will look for files/folders to include/exclude only in the 'path' it is synching to/from.

---

### Post by walmartshopper67 on 2008-07-19
Ah - now that you say that, it makes sense. thanks for the response!:)

---

