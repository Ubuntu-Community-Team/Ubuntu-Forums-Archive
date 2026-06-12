---
title: "Files and Folders copied from CD/DVD are Read Only?"
date: 2005-12-01
forum: General Help
---

### Post by _Ramirez_ on 2005-12-01
All files and folders copied from CD/DVD or mounted NTFS partition are Read Only and I'm wondering if this can be changed. The real reason is: I can't teach this person how to change permisions, it's just too complicated.

---

### Post by sapo on 2005-12-01
whats complicated in hiting ctrl + A to select all files, then right clicking on it, and clickin on the WRITE option in the permissions tab?

---

### Post by cgjones on 2005-12-01
To the best of my knowledge, CD's and DVD's are by their very nature read-only. NTFS is normally mounted read-only for safety, since last I knew, write support for NTFS is sketchy. There might be a way of tweaking a umask to automatically change the permissions when you copy them to a Linux native filesystem.

---

### Post by Jon L. Jacobi on 2005-12-01
Any time you copy a file from CD/DVD, it will be read-only. You can change that once it's on your hard drive, but otherwise you're stuck as far as I know. 

I too was disappointed to find out that NTFS write support is sketchy. From what I've heard, Microsoft has hidden things and not documented it entirely. They've been doing stuff like this forever which is one reason why they gather so much enmity.

On the other hand, it IS their file system...

:rolleyes: 

Cheers, Jon

---

### Post by crispingatiesa on 2005-12-01
Even in windows when you copy a file from a cd it gets copied as read only.

---

### Post by _Ramirez_ on 2005-12-01
It's ok by me that these files are read only, but i've copied some directories and then i couldn't delete them. Did the ctrl+a thing and checked owner write checkbox but that didn't change permisions for files and folders that were in previousely selected folders.

---

### Post by Bachstelze on 2005-12-01
open a terminal and run

```
sudo chmod +w -R /path/to/your/folder/*
```

---

### Post by apoc on 2005-12-01
[QUOTE=HymnToLife]open a terminal and run

```
sudo chmod +w -R /path/to/your/folder/*
```[/QUOTE]

Thanks, I was just searching the forum how to do this :)

---

