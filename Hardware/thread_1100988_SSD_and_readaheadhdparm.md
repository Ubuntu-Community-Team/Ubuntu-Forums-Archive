---
title: "SSD and readahead/hdparm"
date: 2009-03-19
forum: Hardware
---

### Post by non-poster on 2009-03-19
Is there any benefit to having "software read ahead" enable for an SSD?  I would think that it could potentially reduce performance because the drive is wasting time streaming unused data.  There is no seek penalty, so why not just let data be retrieved when it is needed?


man hdparm
...
       -a     Get/set sector count for filesystem (software) read-ahead.  This is used to  improve performance in sequential reads  of  large  files,  by  prefetching additional blocks in anticipation of them being needed by the running task. Many IDE drives also have a separate built-in  read-ahead  function,  which augments this filesystem (software) read-ahead function.

---

### Post by sdennie on 2009-03-19
There is no seek time but, it doesn't read data instantaneously.  Reading 1 byte is probably as fast as reading X bytes (for some value of X) so, why not read X many bytes by default.  There is a decent chance you will need that data anyway.  However, I don't have an SSD so, can't really test it.

---

