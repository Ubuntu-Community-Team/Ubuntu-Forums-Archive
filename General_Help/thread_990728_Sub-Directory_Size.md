---
title: "Sub-Directory Size"
date: 2008-11-23
forum: General Help
---

### Post by mkartic on 2008-11-23
hi, i need to find a way to display the size of my sub directories. I've been suggested a few forms of du but no success so far :confused:

eg: if i have a dir 'a' with b,c,d folders in it, i want to know b,c,d's size alone

ls a
b
c
d


<mysterious command:lolflag:>
b XXXbytes
c YYYbytes
d ZZZbytes


thanks  in advance:)

---

### Post by ciscosurfer on 2008-11-23
You could do something like```
ls -lhR *dirA/*
```Where the directory structure beneath dirA is something like: dirA/dirB/dirC/dirD and you want to recursively list in long-list and human readable format.  This has the added bonus of giving you all file sizes as well.

---

### Post by mkartic on 2008-11-23
> **ciscosurfer said:**
> You could do something like```
ls -lhR *dirA/*
```Where the directory structure beneath dirA is something like: dirA/dirB/dirC/dirD and you want to recursively list in long-list and human readable format.  This has the added bonus of giving you all file sizes as well.

i dont want the file listing, just the directories and their size! :(

---

### Post by ciscosurfer on 2008-11-23
Then using du is your answer.```
du -h ~/Music
```Where ~/Music has a structure like ~/Music/A/B/C/D etc.

---

