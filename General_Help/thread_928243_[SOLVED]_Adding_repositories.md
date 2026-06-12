---
title: "[SOLVED] Adding repositories"
date: 2008-09-23
forum: General Help
---

### Post by Bmtt on 2008-09-23
I'm trying to add a third party repository but it won't let me save it. Please help

---

### Post by spiderbatdad on 2008-09-23
what error message? Are you using "sudo nano" or "gksu gedit" to open the text editor you are using? Hope you are comfortable that this repository will not create conflicts and break your system.

---

### Post by drs305 on 2008-09-23
Here are two wiki pages on repositories, freshly rewritten. One deals with gui (synaptic and software sources), the other via command-line:

[Repositories/Ubuntu (GUI)]("https://help.ubuntu.com/community/Repositories/Ubuntu")

[Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

### Post by spiderbatdad on 2008-09-23
nice wikis...meant to mention the need for adding key is usually required as covered in the wikis.

---

### Post by Bmtt on 2008-09-23
I understand how to add it, but I can't save the file.  It says I don't have permission.

---

### Post by drs305 on 2008-09-23
You have to have adminstrator powers to edit/change sources.list. Using synaptic you use your password to temporarily gain access. 

If you are manually editing the sources.list file with a text editor, open the editor with "gksu", for instance:
```
gksu gedit /etc/apt/sources.list
```

---

### Post by Bmtt on 2008-09-23
That worked.

Thank you!

---

