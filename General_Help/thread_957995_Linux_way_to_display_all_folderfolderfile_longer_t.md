---
title: "Linux way to display all folder/folder/file longer than 250 characters?"
date: 2008-10-24
forum: General Help
---

### Post by Mysticle31 on 2008-10-24
I have a lot of folders with long names.  Some of them can be slimed down by rephrasing them or placing them other places.  

My windows machine running Windows Explorer won't open sub folders when I exceed a certain character limit.

Is there a command or app that will show me all the long folder/file names so I can rename them?

I don't want to have windows machines not be able to access them.  Or WORSE do something like this /Pictures/Trips/2007/Country/blah/blah/**~1**  Which I have seen before.

---

### Post by scragar on 2008-10-24
```
cd
find * | grep ".\{20,\}"
```
replace 20 with any number you want.

EDIT: you might, want to pipe this to less, or put it into a file:
```
**## do it with less(produces a list you scroll using the arrows, space etc, q to exit)**
cd; find * | grep ".\{20,\}" | less
**## store it to a file on the desktop call "too_long.txt"**
cd; find * | grep ".\{20,\}" > ./Desktop/too_long.txt
```

EDIT 2: I've not set it to 250, because there will be more on the file name that just the path from your home directory, you will have the drive name(C:, E:, whatever) and the path through your home folder(eg /home/bob/ ) on top of this that you will have to account for.

---

### Post by Mysticle31 on 2008-10-26
Works Great.  Thanks!

Cool simple little dealy-os like this is why Linux rocks!

---

