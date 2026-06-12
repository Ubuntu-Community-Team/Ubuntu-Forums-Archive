---
title: "Slower speed to copy file"
date: 2011-03-06
forum: Hardware
---

### Post by plenthoz on 2011-03-06
Hey , i'm using ubuntu 10.10 ..I've got issue here ,,,yesterday i copy 3GB video  file from my USB to my notebook...but i've found that everyday the copying speed is getting slower , when i try copy them using win7 it's much faster...can you  help me to boost the copy method??? thanks a lot

---

### Post by JRV on 2011-03-06
Could it be this problem?

Run "top" from the command line.

If "gvfsd-metadata" is hogging your processor do this:

```

rm -rf /home/USERNAME/.local/share/gvfs-metadata
pkill gvfsd-metadata 
```

---

