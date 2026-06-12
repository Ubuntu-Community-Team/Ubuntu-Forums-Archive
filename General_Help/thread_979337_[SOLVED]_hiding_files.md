---
title: "[SOLVED] hiding files"
date: 2008-11-11
forum: General Help
---

### Post by seanksg on 2008-11-11
Is it possible to hide files on Ubuntu; and if so, how?

---

### Post by -Zeus- on 2008-11-11
i assume that you are talking about files in your home directory?  try this:
```
chmod go= /home/username/path/to/file
```

This will set the permissions for group and other to not be able to see, edit, or execute the file, while keeping the permissions for you (the user)

---

### Post by sisco311 on 2008-11-11
Any file or folder whose name is preceded with a period (.) is hidden.

To hide a file rename it: *filename* --> ***.**filename*

---

### Post by seanksg on 2008-11-11
What about on a USB?

---

### Post by Carl Hamlin on 2008-11-11
> **seanksg said:**
> Is it possible to hide files on Ubuntu; and if so, how?

You betcha. Put a period at the beginning of the file name.

---

### Post by -Zeus- on 2008-11-11
on USB, the same will apply *if* it's being read on a Linux/BSD/Mac? operating system.  On Windows, they will be shown.

I guess I overread into this one :lolflag:

---

