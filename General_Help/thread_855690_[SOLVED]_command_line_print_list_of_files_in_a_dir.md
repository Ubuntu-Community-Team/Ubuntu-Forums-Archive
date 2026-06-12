---
title: "[SOLVED] command line: print list of files in a directory to text file"
date: 2008-07-10
forum: General Help
---

### Post by rossdub on 2008-07-10
I'm trying to print the out put of ls -a to somefile.txt.  Any suggestions on how to accomplish this from the command line?

---

### Post by Truedream on 2008-07-10
try ```
ls -R1 /DIR_Name_Here/ > output.txt
```

it'll save the output file in your home folder.

---

### Post by rossdub on 2008-07-10
> **Truedream said:**
> try ```
ls -R1 /DIR_Name_Here/ > output.txt
```

it'll save the output file in your home folder.

Perfect!  Thanks for the quick reply.

---

