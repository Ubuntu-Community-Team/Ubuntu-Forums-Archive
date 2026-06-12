---
title: "Use find with directories with spaces for stdout"
date: 2008-08-08
forum: General Help
---

### Post by Toet on 2008-08-08
I'm trying to change the rights of a number of directories. But some of the directories have spaces in the names. It's only about the directories, not about the files in them.

So far I came up with the next line:

chmod g+rw `find * -type d`

But I notice it cannot handle the dirs with spaces in the names.

How do I handle these dirs aswell?

---

### Post by sisco311 on 2008-08-08
```
find . -type d -exec chmod g+rw {} \;
```

---

### Post by Toet on 2008-08-08
Thanks a lot! That answer made a lot of things clear to me.

---

### Post by sisco311 on 2008-08-08
If your thread is solved, please mark your thread solved by selecting** Mark this thread as solved **from the **Thead Tools**.

---

