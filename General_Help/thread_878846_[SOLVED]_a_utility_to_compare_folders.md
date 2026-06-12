---
title: "[SOLVED] a utility to compare folders?"
date: 2008-08-03
forum: General Help
---

### Post by mahela007 on 2008-08-03
Does anyone outhere know a reliable program which can compare the contents of two folders? I dont need it to modify files to match each other. I only want it to be able to compare all the content of two folders and tell me whether the two folders are the same. It should be able to run on windows. thanks.
(I want it to run on windows because i have some files to compare on a computer which doesnt have ubuntu.)

---

### Post by spin2cool on 2008-08-03
There are several ways to do this.  One would be to use rsync with the '-n' flag.  This does a 'dry-run' and just tells you which files would be synced (because they differ).

Another way would be to write a simple script (bash, perl, ruby, python, whatever) to count the files in each dir, and compare filesize and/or modification date.

---

### Post by spin2cool on 2008-08-03
more specifically, try:

rsync -anhv folder1/ folder2/

note that this will only list what would be copied from folder1 to folder2.  Swapping the folder names will give info on the other way around.

---

### Post by pietjanjaap on 2008-08-03
Install krusader(total commander) there is afunction compare on content.

---

### Post by der_joachim on 2008-08-04
A nice commercial program is [Beyond Compare]("http://www.scootersoftware.com/"), although it may be a bit too much for you. Have you considered using [WinMerge]("http://winmerge.org/downloads/index.php")? It is open source, so I may not be modded down for suggesting BC. :)

---

### Post by mdsharp24 on 2008-08-04
diff -r /folder1 /folder2 > difference

---

### Post by c2olen on 2008-08-04
You can also install Unison, which has support for synchronising windows and unix folders.

---

### Post by mahela007 on 2008-08-04
thanks for helping you guys

---

