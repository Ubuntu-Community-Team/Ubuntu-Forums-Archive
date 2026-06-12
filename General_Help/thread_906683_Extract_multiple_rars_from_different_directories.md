---
title: "Extract multiple rars from different directories"
date: 2008-08-31
forum: General Help
---

### Post by Voorhees1979 on 2008-08-31
Hi all

I ripped my x-files dvds ages ago. I rared them all up. So basically I have this on my hd:

/media/disk/xfiles/s01

in there will be say 20 directories like s01ep01 and so on. I would have to manually go into each folder to unrar the lot which will take ages seeing as there is 9 seasons.

Is there away to somehow select all the folders and some program will go in and unrar them all?

On winblows there is a program called Extract All which does this ( you can add all the folders and it will unrar them all to the same folder, it dont seem to work on wine)

Many thanks for any help

---

### Post by rampageoberon on 2008-08-31
You could write a script to make it extract them all to the current folder.

```
#!/bin/bash
unrar e path_to_file1.rar
unrar e path_to_file2.rar
... and so on ...
```

This will extract all the files in the current directory (check using command "pwd")

Hope that helps

---

