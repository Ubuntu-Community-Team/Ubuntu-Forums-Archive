---
title: "Don't understand help system(s)"
date: 2008-09-12
forum: General Help
---

### Post by Xonara on 2008-09-12
Why are there 3 help systems in the terminal (help, info, manual)? I don't really know how to use them and I just need a comprehensive list of commands a bit like the msdos help command :(

---

### Post by iaculallad on 2008-09-12
> **Xonara said:**
> Why are there 3 help systems in the terminal (help, info, manual)? I don't really know how to use them and I just need a comprehensive list of commands a bit like the msdos help command :(

For comparison, try this in your terminal:

```
man man
man info
```

---

### Post by mb_webguy on 2008-09-12
> **Xonara said:**
> Why are there 3 help systems in the terminal (help, info, manual)? I don't really know how to use them and I just need a comprehensive list of commands a bit like the msdos help command :(

They provide different levels and amounts of information.

If you type "<command> --help" it will give you the basic usage of the command, with maybe a few of the more common options.

If you type "man <command>" it will show you a more comprehensive description of the command and all of its options.

If you type "info <command>", it will sometimes give you the same information as man would, but sometimes give you an even more comprehensive description of the command.

Basically, if you can't remember the basic syntax of a command, then all you need is "<command> --help", and anything more would be overkill.  But if you don't know anything about how a command is used or want to know what the less common options are and how to use them, you need man or info.

---

