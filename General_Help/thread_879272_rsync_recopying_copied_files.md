---
title: "rsync recopying copied files"
date: 2008-08-03
forum: General Help
---

### Post by Serguei_89 on 2008-08-03
Hi,

Here is the problem:

I run this command to backup my data:
rsync -av --no-o --no-g -delete /path/to/source /path/to/destination

but then when it's done, I run the command again and it takes hours!

I'm not sure what it's doing, but it looks like it copies the files again. Like cp. It lists all the files it's going through thinking for a number of seconds about each file. 

Shouldn't it only take a few seconds when I run it the second time?

---

### Post by mdsharp24 on 2008-08-03
Delete everything in the destination and run:

```
rsync --delete-after --exclude-from=exclude -avz /source /destination 
```

Then make a file called exclude and put in it any files folders you want excluded one line at a time

sys
tmp
exclude

---

### Post by DGortze380 on 2008-08-03
> **mdsharp24 said:**
> Delete everything in the destination and run:

```
rsync --delete-after --exclude-from=exclude -avz /source /destination 
```

Then make a file called exclude and put in it any files folders you want excluded one line at a time

sys
tmp
exclude

that will work, but there's an easier way. 

```

sudo rsync -vrlpogxz --delete --progress /source /destination

```

This will keep an exact copy. Add new files, rename existing files that have been changed and delete files that have been deleted, and won't make duplicates. Be sure to change /source and /destination and check man rsync for all the flags to make sure they're exactly what you want.

---

### Post by Serguei_89 on 2008-08-03
> **DGortze380 said:**
> that will work, but there's an easier way. 

```

sudo rsync -vrlpogxz --delete --progress /source /destination

```

This will keep an exact copy. Add new files, rename existing files that have been changed and delete files that have been deleted, and won't make duplicates. Be sure to change /source and /destination and check man rsync for all the flags to make sure they're exactly what you want.

Ok I tried that except for the arguments that preserve permissions. I still see it going through files that it already copied. Same performance.

---

### Post by mdsharp24 on 2008-08-03
-a implies -rlpogx:

man rsync| grep -a

-a, --archive               archive mode; same as -rlptgoD (no -H, -A)

---

### Post by Serguei_89 on 2008-08-03
Ok I timed my commands and it is much shorter when I repeat the syncing.
I guess it takes time for it to compare files and realize that it already copied everything. 

I thought it would be quicker though. When syncing a small change within a pool of 80GB of data, it takes an hour or two just to go through the checking.

---

### Post by Serguei_89 on 2008-08-03
Actually, it's not much shorter.

I deleted everything in a smaller destination folder and it took 2:14 minutes

The repeat of the command took 1:42.

What's going on?

---

### Post by DGortze380 on 2008-08-03
> **Serguei_89 said:**
> Actually, it's not much shorter.

I deleted everything in a smaller destination folder and it took 2:14 minutes

The repeat of the command took 1:42.

What's going on?

rsync still checks ALL the files, but will not necessarily make a change to all the files. my 111GB drive (about 65GB of data) takes about 55 minutes. Also depends on your system and what other processes are running.

I got tired of it taking so long and adjust what I really need backed up. For me, really just my home directory. If you're just backing / think about backing up only the sub-directories that you need.

---

### Post by Serguei_89 on 2008-08-03
Yes, there is still some inevitable time for checking, but I think i figured out something else:

Displaying the progress and generally outputting things to console takes time. the 1:42 minutes I measured became 2 seconds when I took out --progress and -v options.

---

### Post by DGortze380 on 2008-08-03
> **Serguei_89 said:**
> Yes, there is still some inevitable time for checking, but I think i figured out something else:

Displaying the progress and generally outputting things to console takes time. the 1:42 minutes I measured became 2 seconds when I took out --progress and -v options.

that;s good to know. I like what to know whats going on so I never thought of taking out progress and verbosity.

---

