---
title: "Entering a folder with space in the name"
date: 2008-09-13
forum: General Help
---

### Post by zpzpzp on 2008-09-13
Hi

I can't seem to enter folders with spaces in the folder name in the terminal. For example:

botwood% ls
Desktop  Library   My Documents  Sent	Win	       mail	 winold
Drafts	 ModelSim  Pictures	 Trash	amsn_received  print.ps  winxp
botwood% cd My Documents
ksh: cd: bad substitution
botwood% 

Does anyone know how to get around this?

Thanks a lot.

Paul

---

### Post by Patrick793 on 2008-09-13
You need a \ before a space, so to cd to My Documents, it would look like this.
```
cd My\ Documents
```

---

### Post by eggdeng on 2008-09-13
Alternatively, just use quotes
```
cd 'My Documents'
```

---

