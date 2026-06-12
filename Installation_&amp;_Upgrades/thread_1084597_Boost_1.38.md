---
title: "Boost 1.38"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by sirjanselot on 2009-03-02
Ubuntu doesn't have packages yet for boost libraries above 1.35.

Unfortunately, I have software that requires a boost version to be 1.38.

I installed it, using ./configure make install and put it in a user defined folder: /home/(my username)/pool.

The trouble is when I'm compiling the software: [http://mathema.tician.de/software/hedge](http://mathema.tician.de/software/hedge), it cannot find it.

I tried to use the export command: export LD_LIBRARY_PATH=$HOME/(my username)/pool/lib:${LD_LIBRARY_PATH}

and that didn't work.  

I also tried editing my ld.so.conf and added my user defined folder: /home/(my username/pool/lib

but it still won't look in there.

Any thoughts?

Thank you!

Jan

---

