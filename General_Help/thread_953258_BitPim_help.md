---
title: "BitPim help"
date: 2008-10-20
forum: General Help
---

### Post by getnripped on 2008-10-20
I need help I get this error when trying to run BitPim



> Another copy of BitPim is using the same data dir:
/home/runman/.bitpim-files

---

### Post by shawnrgr on 2008-10-20
sounds like its already running in the background

```
killall bitpim && bitpim &
```

---

### Post by Bakon Jarser on 2008-11-06
I get this message to and that command didn't help.  I can't find it running in system monitor either.

---

### Post by tardy on 2008-12-26
I just encountered this issue myself, it looks like all you need to do is find the file ".lock" and remove it.

this should work

```

rm ~/.bitpim-files/.lock

```

---

