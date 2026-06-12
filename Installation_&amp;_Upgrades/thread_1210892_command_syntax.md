---
title: "command syntax?"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by archangel2021 on 2009-07-12
so for the life of me, i can't get this syntax figured out.

What is the command syntax to extract a specific file or folder out of a tar ball. ( tag.gz exactly ) ?????????????????????  I just can't :(

---

### Post by JohnnySage50307 on 2009-07-12
The command you want is as follows:
"
$ tar xvzf *package*.tar.gz       |         *for gzip files*
$ tar xvjf *package*.tar.bz2      |         *for bzip2 files*
"

This was taken from the Linux Pocket Guide by Daniel J. Barrett; it's published by O'Reily, and I highly sugest it to anyone who's new.  I've been working on Linux machines for about 4yrs now, and I keep that book in my laptop bag for whenever I can't remember anything!  It's like $10 at B&N

---

### Post by unlimitedz on 2009-07-12
May be useful, to see the correct syntax for a command:
```
man tar
```

---

