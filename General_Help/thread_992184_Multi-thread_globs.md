---
title: "Multi-thread globs?"
date: 2008-11-24
forum: General Help
---

### Post by Mazin on 2008-11-24
I regularly run batch operations.  For example, I convert all the ppm files in a directory to pngs with "mogrify -format png *.ppm".  Is there an easy way to split this into multiple parallel operations?  I have a quad-core processor, and being able to run 4 instances of this would speed things up tremendously.

Is there perhaps a bash script or something that'll automatically divide a globbed task into several tasks?

---

