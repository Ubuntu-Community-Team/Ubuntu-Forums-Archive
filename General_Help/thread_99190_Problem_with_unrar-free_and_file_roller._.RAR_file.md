---
title: "Problem with unrar-free and file roller. .RAR files won't open"
date: 2005-12-05
forum: General Help
---

### Post by gizm0 on 2005-12-05
I just installed unrar-free, but i still can't unrar .rar files. Unrar-command does not work and file-roller does not recognize .rar files.

So what am i doing wrong?

I got newest Ubuntu and AMD64.

---

### Post by Arktis on 2005-12-05
Try the Package p7zip and after installing use:

```
7z x /path/to/archivename.rar
```

---

### Post by gizm0 on 2005-12-05
But can i add it to file-roller some how?

---

### Post by hw-tph on 2005-12-05
unrar-free supports RAR files up to and including the 2.x series compression algorithms. RAR version 3.0 and later uses a proprietary algorithm (unless you force it to create backwards compatible archives). Use unrar-nonfree instead, you can find it in Ubuntu multiverse.


H&#229;kan

---

### Post by gizm0 on 2005-12-05
As i said ....i HAVE unrar-free installed, but it won't work. When i type unrar or unrar-free it says: "command not found" and file-roller cannot find unrar-free. It just says "rar is not supported" or something like that. But it can find manual pages about unrar-free, with command man unrar-free.

---

### Post by gizm0 on 2005-12-05
Hmmm...that was pretty weird problem. I needed to add different repository. The other one just installed manual pages for unrar-free.

Anyways...now it works :).

---

