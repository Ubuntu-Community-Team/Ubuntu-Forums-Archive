---
title: "what is the point of the archiver?"
date: 2008-08-06
forum: General Help
---

### Post by Howitzer777 on 2008-08-06
when i download a tar.gz file for example that will show be the thing it runs on. what do i do with it? if i press the extract button nothing really happens.

---

### Post by Sydius on 2008-08-06
When you press "Extract," a window should appear that has you select a folder.  It is in the folder you select that you will find the extracted files.

Also, from a shell, you can try:

```
tar -xf thefilename.tar.gz
```

It will extract the file(s) to the current directory without the need for the GUI archive program.

---

### Post by Locutus_of_Borg on 2008-08-06
it is a "pretty" GUI to perform the 'tar -xzf $f' command

---

