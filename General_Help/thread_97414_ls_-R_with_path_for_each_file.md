---
title: "ls -R with path for each file?"
date: 2005-11-30
forum: General Help
---

### Post by Kevinator on 2005-11-30
I want to perform some operation on every file in a directory, including files in sub-directories. ls -R will obviously give a list of all the file names, but it's not in a format which can easily be used for this purpose. Is there a simple way to format this list so that each file is preceded by its path? Or is there perhaps a tool that is more suited to this task?

Thanks.

---

### Post by amohanty on 2005-12-01
find *
at the top of the foldre tree where you want to do the operation
This will not return hidden files (files startting with a .). To get all files

find

HTH
AM

---

### Post by Kevinator on 2005-12-01
That looks like a very useful command that should do the job nicely. Thank you very much.

---

