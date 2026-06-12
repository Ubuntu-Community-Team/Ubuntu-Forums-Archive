---
title: "vi with colours but no new window"
date: 2005-11-04
forum: General Help
---

### Post by pickarooney on 2005-11-04
How do I make it so when I open a file from the console with **vi** it edits the file, with colurs, in the same window?
Under Mandrake, vi was an alias for gvim, but in Ubuntu when I gvim a file, it opens a new (white) editor window which takes several seconds to load.

---

### Post by rmjokers on 2005-11-04
You probably want to be using vim.  I am not sure that plain old vi actually supports colors.  If, after trying this you still dont have color, you may need to add this:

syntax on

to your .vimrc file in your home directory.

---

### Post by ranf on 2005-11-04
[QUOTE=pickarooney]How do I make it so when I open a file from the console with **vi** it edits the file, with colurs, in the same window?
[/QUOTE]
```
echo "syntax on" >> ~/.vimrc
```

---

### Post by pickarooney on 2005-11-04
:KS 

sorted, thanks

---

