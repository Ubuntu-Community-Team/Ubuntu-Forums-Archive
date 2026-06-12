---
title: "[SOLVED] tail command bug?"
date: 2008-08-11
forum: General Help
---

### Post by sadams6696 on 2008-08-11
Greetings All!
We recently upgraded from 6.06 LTS to 8.04 LTS and noticed the following previously successful form of the tail command no longer works:

tail +5 foo.bar

According to the man page,  -n, --lines=N should:
output  the last N lines, instead of the last 10; or use +N to output lines starting with the Nth.

Is this a bug or a "feature" of the new release?

---

### Post by pauper on 2008-08-11
"tail +number /path/to/file" has been deprecated, new syntax as follows
"tail [highlight]-n[/highlight] +number /path/to/file".

[edit:]

This will bring back the old behavior:

```
export _POSIX2_VERSION=199209
```

Source:
[http://www.gnu.org/software/coreutils/manual/coreutils.html#Standards-conformance](http://www.gnu.org/software/coreutils/manual/coreutils.html#Standards-conformance)

---

### Post by sadams6696 on 2008-08-12
Thanks pauper. I'm beginning to hate that word... deprecated...  Seems the --lines= works too, but either way, I have hundreds of scripts to change!

---

