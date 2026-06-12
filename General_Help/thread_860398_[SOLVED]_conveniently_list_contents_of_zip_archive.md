---
title: "[SOLVED] conveniently list contents of zip archive?"
date: 2008-07-15
forum: General Help
---

### Post by raymondvillain on 2008-07-15
Running Hardy on a desktop, new to Ubuntu.

Downloading lots of data from coworkers and it is always in a zip file.  I would like to create a text file with the names of the individual data files that are contained within a particular archive, or *.zip file.

Is there an easy way to do this?  From a terminal window, perhaps?

Presently I have to type the name of the archive file in a word processor, use archive manager to view the contents, and then type the name of each individual file in the archive.  Very slow.

Does anyone have any suggestions?

Thanks in advance.

---

### Post by bodhi.zazen on 2008-07-15
From the command line :

```
unzip -l
```

[http://linux.die.net/man/1/unzip](http://linux.die.net/man/1/unzip)

---

### Post by CatKiller on 2008-07-15
There may be a command-line tool for manipulating zip files that has the option of listing the contents of an archive. Possibly 7-Zip can do this? I've never used it.

In the meantime, a possible optomisation for you would be to use the View -> Last Output option to copy-and-paste the filenames into a text document.

EDIT: Like the tool that bodhi.zazen describes... I am both uninformed and slow :(

;)

---

### Post by issih on 2008-07-15
You can also squirt the output directly into a file using the redirection operator.

```
unzip -l inputFile.zip > outputFile.list
```

---

