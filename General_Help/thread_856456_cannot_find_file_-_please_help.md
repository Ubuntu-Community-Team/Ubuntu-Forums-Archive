---
title: "cannot find file - please help"
date: 2008-07-11
forum: General Help
---

### Post by ukdeveloper on 2008-07-11
Hi,

I have ubuntu installed on a dedicated server.

my used disc space was 27gb and i wanted to backup a lot of files to download to a local machine.

I used webmin to create a .tar file of the required directory containing the files i wanted to download.

Now my used disc space shows 40Gb so i know the file has been created but for the grace of god I cannot find this file anywhere. It didnt give me the option to name the file.

Is there a command i can run to search the entire server for all files over (for instance) 3gb? that way it should recover the file i am looking for.

Or is there another way?

Regards

Carl.

---

### Post by dracayr on 2008-07-11
execute

```
cd /
sudo du --max-depth=1 --all 
```

from a terminal. all folders and files in / will be listed, and their sizes. you can easily find the biggest folder. then cd into that folder:

```
cd *foldername*
```
execute the sudo du --max-depth=1 --all again to track down the big file

dracayr

---

