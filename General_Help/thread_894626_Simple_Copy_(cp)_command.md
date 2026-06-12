---
title: "Simple Copy (cp) command"
date: 2008-08-19
forum: General Help
---

### Post by cnic on 2008-08-19
Trying to run a copy command: cp (cp Testdocument /newhome) Near as I can tell I'm using the right format, but bash reports that there is "no such file or dirctory."  The file, TestDocument, is in my home.  Would think permissions wouldn't be a problem.

---

### Post by jerome1232 on 2008-08-19
Does the directory exist? cp won't create new directories for you.

---

### Post by finer recliner on 2008-08-19
i think that the location '/newhome' does not exist yet.

you can create a new directory using the mkdir command see the man page for more help

also, i wouldnt recommend making a new directory off of /, i assume you were trying to make a new subdirectory from your home directory. you would want to type /home/<user>/newhome

---

