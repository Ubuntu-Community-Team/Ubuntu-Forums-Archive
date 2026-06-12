---
title: "How do i grant access to files from ohter computer?"
date: 2008-11-01
forum: General Help
---

### Post by Jepperen on 2008-11-01
Hey

I have coded some parts of a website on my laptop which have Ubuntu installed. Then i have copy the files on to a USB memory stick and now i want to copy them to my desktop computer, which also have Ubuntu installed.

First i had to do chmod 777 to the folder, so i could copy the files from the stick to the desktop pc. But now when i try to open the files in a browser i get permission deny error. How do i change the permission on all files in a folder? Didnt work with chmod on the folder.

---

### Post by m_l17 on 2008-11-01
You only changed the permissions for the folder not the contents.

In order to set the permissions of a directory and all the files in that directory, you'll need the -R option:

```
$ chmod -R 777 somedir/
```

---

