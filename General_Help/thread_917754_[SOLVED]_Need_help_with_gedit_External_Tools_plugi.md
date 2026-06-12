---
title: "[SOLVED] Need help with gedit External Tools plugin"
date: 2008-09-12
forum: General Help
---

### Post by Idefix82 on 2008-09-12
Dear all,
I am configuring gedit to be my main editor for MAGMA (a mathematics package). I wrote an external tool which executes the current file in MAGMA, but I want to automatically append the exit; command and the end of the file before executing it. Is there a way to use the external tools plugin to modify the document by appending a line at the end?
Thanks!

---

### Post by Idefix82 on 2008-09-12
If anybody is interested, I solved it by
```
echo 'exit;' >> "$GEDIT_CURRENT_DOCUMENT_NAME"
```

I tried to use the cat command, i.e.
```
cat >> "$GEDIT_CURRENT_DOCUMENT_NAME"
exit;
^D
```
but couldn't figure out how to input Ctrl-D in the external tools definition. If you have any ideas, I would still be interested to hear them!

---

