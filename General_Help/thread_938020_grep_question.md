---
title: "grep question"
date: 2008-10-04
forum: General Help
---

### Post by torrent478 on 2008-10-04
or at least I think its grep I need to be using...

I need to get a list of all the absolute pathways of every file in a single folder (300+ files) and have them piped into a text document.

I've done it before but its been a really long time and I have no idea what to do anymore :'(

If anyone has any ideas it would be greatly appreciated!


Thanks =)

---

### Post by Calmatory on 2008-10-04
Well, ```
ls | tee files.txt
```
writes the output of ls to a file, but I do not know the flag to show the absolute path of the files. Fast browsing trough "ls --help" didn't give me an answer. :|

---

### Post by Yannick Le Saint kyncani on 2008-10-04
> **torrent478 said:**
> I need to get a list of all the absolute pathways of every file in a single folder (300+ files) and have them piped into a text document.

find /path/to/your/files/ -type f >/your/output/file.txt

---

### Post by mike2357 on 2008-10-04
I think the "find" command will do the trick for you.  If the directory you want to search is "/home/username/stuff", the command would be:

find /home/username/stuff -maxdepth 1 -type f -print > OUT

-maxdepth 1 prevents "find" from going into sub-directories, which is its default.

-type f means to restrict the search to regular files, as opposed to links, directories, etc.

Run "man find" for a lot of good information.

---

### Post by torrent478 on 2008-10-04
thanks a lot :D

it worked perfectly :KS

---

