---
title: "Command line backup"
date: 2008-09-14
forum: General Help
---

### Post by bzachd on 2008-09-14
Hi,

Wondering if anyone knows how to backup a directory from the command line. I was going through a tutorial that lists 
tar cvf data.backup /data  where data.backup is the folder you want to store a backup of the directory data. Any ideas? also is there one that I can use to backup individual files to a folder via the command line.

Thanks,
Zach

---

### Post by cyclobs on 2008-09-14
you can tar or zip the directory

tar -cvvf <name of tar>.tar <directory to tar>

---

### Post by Hooya on 2008-09-14
Depends on the directory.  For instance, if you are trying to backup your entire /home directory you're going to miss a lot of stuff unless you use a fairly complicated syntax.  In that instance, take a look at tutorials dealing with moving your /home directory to a new partition.  Should be easy enough to find via Google.

So while many directories can be simply zipped up, it may be more complicated, so know what you're getting into, and know what you can and cannot do with the "cp" command.

---

### Post by bzachd on 2008-09-14
cyclobs,

Thanks, I ran a quick test and it did work. I wanted to try to learn the command lines to see what its doing before just using the GUI.

Thanks,
Zach

---

### Post by bzachd on 2008-09-14
Hooya,

Good advice.. I will do that

Thanks,
Zach

---

