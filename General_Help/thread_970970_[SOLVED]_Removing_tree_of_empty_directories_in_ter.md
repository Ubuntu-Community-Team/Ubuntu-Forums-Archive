---
title: "[SOLVED] Removing tree of empty directories in terminal"
date: 2008-11-04
forum: General Help
---

### Post by jakupl on 2008-11-04
This is probably a stupid question, but how do i, in one command, Remove a tree of empty directories and subdirectories, in the terminal?

---

### Post by jakupl on 2008-11-04
jup it was stupid.

```
rm -rf *
```

---

### Post by bodhi.zazen on 2008-11-04
:lolflag:

Careful with that -rf *

Best specify the parent directory with a full path.

```
rm -rf /home/user/parent
```

---

### Post by jakupl on 2008-11-04
> **bodhi.zazen said:**
> :lolflag:

Careful with that -rf *

Best specify the parent directory with a full path.

```
rm -rf /home/user/parent
```

yeah, i know. Thanks.

---

