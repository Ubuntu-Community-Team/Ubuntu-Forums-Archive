---
title: "editor for gftp"
date: 2008-09-29
forum: General Help
---

### Post by Cool Surfer on 2008-09-29
When I use gftp, and try to edit a file, i get a message to first select an editor.

How to do this pl.

---

### Post by niteshifter on 2008-09-29
Hi,

With gFTP up, press Ctrl+O (or click FTP on the menu, then click Options).
In the dialog that appears, under the General tab:
Enter the path to the editor program you wish in the box by "Edit Program".

See attached screenshot.

---

### Post by Cool Surfer on 2008-09-29
yes I know till here. What to put in path?

---

### Post by kpkeerthi on 2008-09-29
Which editor do you want to use?

---

### Post by Cool Surfer on 2008-09-29
> **kpkeerthi said:**
> Which editor do you want to use?


I dont know which all editors we havein ubuntu, like notepad in windows

---

### Post by kpkeerthi on 2008-09-29
gedit is your best bet. Fill the editor path with /usr/bin/gedit like in the screenshot above.

To find the path of an editor program use **which** command, like so (for gedit):

```
which gedit
```

---

