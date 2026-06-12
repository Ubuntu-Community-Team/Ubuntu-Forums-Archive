---
title: "Why doesn't rm --dry-run exist?"
date: 2008-08-18
forum: General Help
---

### Post by pedrogfrancisco on 2008-08-18
The idea struck me from nowhere and I find it weird nobody has asked this before but...

How come nobody remembered to create an option to rm which would allow one to see the effect of the rm command but without actually doing it?

```
rm -s some_dir_to_be_deleted/
```
or/and
```
rm --dry-run some_dir_to_be_deleted/
```


from apt-get's man page:
>  -s, --simulate, --just-print, --dry-run, --recon, --no-act
           No action; perform a simulation of events that would occur but do
           not actually change the system. (...)


---

### Post by Oldsoldier2003 on 2008-08-18
Probably because rm  has the -i and -I flags... a --dryrun or --simulate would be pretty useless for exceptionally large directories.

Thats just my personal take on it.

---

### Post by pedrogfrancisco on 2008-08-18
You clearly haven't deleted all your Desktop's files because you were too lazy to write the whole directory name (yes it doesn't make sense, but it did happen ;) )

Plus on out-of-the-box things, like for instance, deleting all hidden files in a directory, a --dry-run option would be very nice...

Most people I know the first time that tried to delete all hidden files through the console made rm go to the parent directory and so on.....

---

### Post by Too Late on 2008-08-18
I agree. It would be very nice feature! Yes, the -i option can do quite the same thing, but it's not very nice to press 'n' and 'enter' all the time. In addition, you have to press 'y' and 'enter' when it asks the "descend into directory" question.

---

### Post by pedrogfrancisco on 2008-08-18
On second thought, one can test the correctness of one syntax doing an ls with the same string.

Which on the above example would be:
```
ls -lR ./.??*
```
to confirm that the string actually did what was expected (taken from [here]("http://www.labtestproject.com/linuxcmd/rm.html"))

---

### Post by akabdog on 2008-11-14
You could also use 
#yes no | rm -ri *
this will work similarly to a dry run, it's automatically answering 'no' at the prompts

---

### Post by spibou on 2008-11-14
But this way rm will not descend into directories at all so you won't get to see what it would erase inside those directories.

---

### Post by Denestria on 2008-11-14
> **pedrogfrancisco said:**
> You clearly haven't deleted all your Desktop's files because you were too lazy to write the whole directory name

If you were too lazy to to enter the whole directory then you're probably going to be too lazy to do a --dry-run before actually executing the command.

---

### Post by spibou on 2008-11-14
> **Denestria said:**
> If you were too lazy to to enter the whole directory then you're probably going to be too lazy to do a --dry-run before actually executing the command.
Not to mention actually reading the output of the dry run ;-)

---

### Post by geirha on 2008-11-14
You can use find to delete recursively.
```

find /some/path         # Lists what will be deleted, add -ls to get a listing like "ls -l"
find /some/path -delete # Delete.

```

---

