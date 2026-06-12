---
title: "Terminal Syntax Problem"
date: 2008-08-14
forum: General Help
---

### Post by change_mode on 2008-08-14
I want to use this command on some files

rename -v 's/123//' *

to remove the 123 part from any file names. But instead of 123 I want it to remove [].
How do I get the terminal to accept the command? Just using [] instead of 123 gives me a syntax error.

---

### Post by change_mode on 2008-08-15
Anyone? :confused:

---

### Post by tacutu on 2008-08-15
```
rename -v 's/\[\]//'
```

---

### Post by pauper on 2008-08-15
```
rename -v 's/\[//; s/\]//' *
```

[edit:]

Or:

```
rename -v 's/\[*\]*//g' *
```

---

