---
title: "User put a Root owned folder in Trash..."
date: 2008-08-14
forum: General Help
---

### Post by LeoSolaris on 2008-08-14
Alright....  This seems sorta silly to me, but I managed to put a folder in my user Trash that had a root owned folder in it. Now trash will not delete it and I cannot get it back out of trash to be able to delete it with ```
gksudo nautilus
```

Added to that, now the root Trash is not able to open.   It gives a pop up window with an error that reads ```
The folder contents could not be displayed. Sorry, couldn't display all the contents of "trash": Operation not supported
```

I just noticed when I closed the root nautilus terminal said this: ```
 ** (nautilus:9725): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
--- Hash table keys for warning below:
--> trash:///

(nautilus:9725): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:9725): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

```

I am a little lost.

---

### Post by drs305 on 2008-08-14
normally i recommend:
```

gksu nautilus $HOME/.local/share/Trash

```
and just delete the 'files' and 'info' folders.

For root's trash:
```

gksu nautilus /root/.local/share/Trash

```
and just delete the 'files' and 'info' folders.

**Use "gksu" or "gksudo" rather than "sudo" for graphical apps.** Using "sudo" with nautilus or other such apps can create problems. Save "sudo" for commands executed in terminal which don't open gui-based apps.

If you still can't get rid of them:
```

sudo chown -R *username *$HOME/.local/share/Trash
rm -r $HOME/.local/share/Trash

```

---

### Post by KeybladeSephi on 2008-08-15
I have the same problem. I can delete the files from the trash bin with the codes drs305 had already mentioned, but I still get the error you have, LeoSolaris. Does anyone have any ideas on how to fix this problem?

---

### Post by LeoSolaris on 2008-08-15
Thank ya! I manged to delete the offensive trash, from both user and root.

I am still getting that error when I try to open root trash, though.

Strange.

---

### Post by Byb on 2011-12-21
Sorry to dig out such an old topic, although it is a very interesting and is the most relevant on the first page of my google query.
I also meet the issue of gksudo nautilus won't display Trash content (from the ootb bookmark). Thanks to this topic I can see the deleted files and related info in the /root/.local/share/Trash folder, but I'd like to know if I have something misconfiged ( place trash:/// error: [SIZE=2]**Unable to display the folder content.**[/SIZE] Sorry, unable to the whole content of « trash » : Operation not supported *roughly translated from french - sorry-myself* ;) ) before I post a ~bug~ in launchpad, because it is not very handy (maybe impossible) to rebuild a tree that was pruned in random time order with these info, when the handy Trash view allows to sort by deletion timestamp.
for info:
```
root@pc:~/.local/share# ls -la Trash
total 16
drwx------  4 root root 4096 2011-01-05 19:50 .
drwx------  6 root root 4096 2011-12-21 11:02 ..
drwx------ 30 root root 4096 2011-12-21 08:14 files
drwx------  2 root root 4096 2011-12-21 08:14 info
```
Thanks for comments 

BTW, a tip to switch back from Ctrl+L shortcut ("Go to") display?

---

