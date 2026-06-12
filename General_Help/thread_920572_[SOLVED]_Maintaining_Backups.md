---
title: "[SOLVED] Maintaining Backups"
date: 2008-09-15
forum: General Help
---

### Post by verbal.kint on 2008-09-15
i have a sizeable amount of music on my harddrive which i also have backed up on external harddrive and i'm looking for a way to update the backup more efficiently.

At the moment i just delete the old folder and copy over the more recent version from my laptop. I prefer to do this than to copy the folder on top of the old one and constantly tell it to not overwrite because it means i can just let it run and go away for a while.

So basically what i want is something that will delete files that arent in the original folder anymore and copy over files that are new, thus optimizing the process and speeding it up considerably.

anyone got any ideas??


Forever Thankful
Roger "Verbal" Kint

---

### Post by Infinite Indefinite on 2008-09-15
Have you tried flyback?  

You can get the details here:

[http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10](http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10)

---

### Post by vanadium on 2008-09-15
```

rsync -av --delete <source> <backup>

```

will copy only the updated files over and delete files in the destination that do not anymore exist in the source without user intervention.

---

### Post by hwttdz on 2008-09-15
Of course vanadium beat me to it and has a better solution, so I'd do what (s)he says.  Also that's super clever, and I'm going to be using it a lot.  How's it do on bandwidth usage if remote?

For adding new files to the backup you can do 
cp -u
which replaces the files if newer, so it would only do any grunt work if you've changed the file and it will only copy a small fraction of files, which would make it very fast.  

To remove the old ones, I would go for a bash or perl script that listed the contents of the backup directory, and then changed the paths and checked for existence in the live directory, and if the file did not exist in the live directory it would delete them.  Something like:

$path_to_live
$path_to_backup
$curr_file

if does not exists $path_to_live/$curr_file
delete $path_to_backup/$curr_file

---

### Post by swisscow on 2008-09-15
Alternatively use Unison - in the repos. GUI based version of rsync and works sweet.

Only thing as you are using an external Hard drive add 

perms=0

to the profile in the hidden unison folder in your home folder

---

### Post by vanadium on 2008-09-15
That is not entirely correct: unison is a utility on its own, that has a particular feature: it can synchronize different directories, i.e. make them similar after different work has been done on each of them. It obviously can mirror as well.

Also rsync has a graphical shell: grsync.

---

### Post by verbal.kint on 2008-09-16
OK thanks guys, i tried rsync and unison and both of them seem to do the job i'm looking for.

---

