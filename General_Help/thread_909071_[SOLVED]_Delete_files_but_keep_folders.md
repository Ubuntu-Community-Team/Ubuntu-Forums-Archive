---
title: "[SOLVED] Delete files but keep folders"
date: 2008-09-03
forum: General Help
---

### Post by taecha on 2008-09-03
Hi everybody.

Does anybody know how I can delete files recursively but keep the folders?

Thanks for the help.

---

### Post by hyper_ch on 2008-09-03
you'll have to do that with the command line. You'll need to use "find" to find only files and then pass the argument to a rm command.

---

### Post by Beth1957 on 2008-09-03
> **hyper_ch said:**
> you'll have to do that with the command line. You'll need to use "find" to find only files and then pass the argument to a rm command.

Is it OK to just open the folder(s), CTRL+click the files, & then just move them to te deleted items folder?

---

### Post by hyper_ch on 2008-09-03
that you would have to do for each folder ;) depending on the amoung it can get tiresome ;)

---

### Post by iaculallad on 2008-09-03
> **taecha said:**
> Hi everybody.

Does anybody know how I can delete files recursively but keep the folders?

Thanks for the help.

Would that be (Just be sure that you're in the parent directory):

```
find . -name *.* -exec rm -f {} \;
```

---

### Post by Beth1957 on 2008-09-03
> **hyper_ch said:**
> that you would have to do for each folder ;) depending on the amoung it can get tiresome ;)

:lolflag: I guess it could at that! I'm still a bit wary of the command line, that's my problem :wink:

---

### Post by hyper_ch on 2008-09-03
Beth: The command line is your friend ;)

---

### Post by justleen on 2008-09-03
> **iaculallad said:**
> Would that be (Just be sure that you're in the parent directory):

```
find . -name *.* -exec rm -f {} \;
```

how bout ```

find . -type f -exec rm -f {} \;


```

that will delete all file, not just the ones with "conventional" names like "files.ext"

---

### Post by roelpeeters on 2008-09-03
How about:
```

find . -type f -delete

```

This will delete all files (that is what -type f does)

- Roel.

---

### Post by hyper_ch on 2008-09-03
and before you run it with "rm" rather use an echo first ;) just to be sure

---

### Post by ilrudie on 2008-09-03
> **roelpeeters said:**
> How about:
```

find . -type f -delete

```This will delete all files (that is what -type f does)

- Roel.

Before you ask questions about what a flag does you can always just read the man page for the command.  in this case type man find into the terminal and it will tell you all about find.  this works for most cli commands.  to find what -type does enter /-type once you are reading the man page and it will find -type and take you to it.  hit n to go to the next instance of -type.  hit q to leave the man page.

short answer: "-type f" means only find files

---

### Post by taecha on 2008-09-03
Thanks everybody for the help. I got the idea.

---

### Post by Beth1957 on 2008-09-05
> **hyper_ch said:**
> Beth: The command line is your friend ;)

I'm slowly getting braver, Hyper_ch :wink: - with a great deal of help from this fantastic community!

---

### Post by taecha on 2008-09-05
Can't agree more. I have also learnt that you can save a lot of time - and mouse moving for that matter ;-) - by making use of bash. It's usually intimidating for the newbie but really a great tool once you get used to it. And as Beth said, the community is great help, indeed.

Once again, thanks to all of you.

---

