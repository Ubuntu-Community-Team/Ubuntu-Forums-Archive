---
title: "[SOLVED] Infinite shortcuts of desktop folder !!!!"
date: 2008-07-15
forum: General Help
---

### Post by cmb11 on 2008-07-15
I created a shortcut of the Desktop folder on the Desktop by mistake!! so now when I go to this shortcut I find another Desktop folder in it and so on...

/home/cmb11/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop....

So I deleted this folder and when I empty the trash it will automatically regenerate because of the infinite loop of creating a shortcut of desktop in each desktop folder :confused: :P So basically the Trash is always full :confused:

so plssss could you give me a way to cut this loop and finally delete all these folders!!!!!!!!

---

### Post by CatKiller on 2008-07-15
It must be said that I don't understand why emptying the Trash would recreate the shortcut. However, ```
rm Desktop/Desktop
``` might remove the shortcut, without it going to the Trash. It would be worthwhile to make sure that there's nothing else on the Desktop first. If that doesn't work, then ```
rm Desktop
``` possibly followed by logging out and logging back in may remove the Desktop and allow it to be recreated, empty.

I have never tried either of these.

It used to be the case that moving anything to Trash in reality simply moved it to a folder, called ~/.Trash. I understand that this has changed with the latest version of Ubuntu. I don't know where the contents of the Trash are now stored.

---

### Post by cmb11 on 2008-07-15
Thank you CatKiller, I managed to get rid of the shortcuts on my desktop, but I still have the same problem with the ones in my Trash (from my first attempt to delete the files)! :(
the path to the trash files in ubuntu hardy is: 
/home/gap/.local/share/Trash/files/

So now i have this:
/home/cmb11/.local/share/Trash/files/Desktop/Desktop/Desktop...

I can't find a way to empty my trash! Each time I empty it, I get a dialog showing that 2000 files have been deleted... but the files will keep on regenerating in the trash. I tried to cut the shortcut from the trash back to my desktop and then deleting it using "rm" but even when I move it, the trash will keep on generating the same files as before...
So as a final attempt, I tried to delete the Trash but I'm getting the following msg: 

Error while deleting.
There was an error getting information about the files in the folder "Desktop".
Error stating file '/home/gap/.local/share/Trash/files/Desktop.2/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop..........

so do you have a solution for that ???? :confused::confused::confused:

Thank you for helping me..

---

### Post by cmb11 on 2008-07-15
So basically i have to cut that loop that keeps on generating files.. and then delete the main file from the trash.. So is there a way to do that ?

---

### Post by cmb11 on 2008-07-16
Helllllppppp !!!!! :(:(:(

---

### Post by CatKiller on 2008-07-16
> **cmb11 said:**
> the path to the trash files in ubuntu hardy is: 
/home/gap/.local/share/Trash/files/

So you could remove that directory with ```
rm ~/.local/share/Trash/
```

---

### Post by cmb11 on 2008-07-16
yup I tried that but I'm getting this msg:

:~$ rm ~/.local/share/Trash/
rm: cannot remove `/home/gap/.local/share/Trash/': Is a directory

So I went to that directory and i tried to delete the Trash with the "delete" option (bypass the trash) but I'm getting the following msg:

Error while deleting.
There was an error getting information about the files in the folder "Desktop".
Error stating file '/home/gap/.local/share/Trash/files/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop..........

---

### Post by Cone on 2008-07-16
> **cmb11 said:**
> yup I tried that but I'm getting this msg:

:~$ rm ~/.local/share/Trash/
rm: cannot remove `/home/gap/.local/share/Trash/': Is a directory


Try "rm -R ~/.local/share/Trash" for a recursive delete (how you remove folders and everything within them)

---

### Post by brokenLockpick on 2008-07-16
what about dragging and dropping the desktop link into a folder like documents? may get rid of the looping behavior

---

### Post by cmb11 on 2008-07-16
Hey Cone thanks a lot for your answer!! the "rm -R" command solved the issue:)


Thank you CatKiller, Cone and brokenLockpick for your help..

:):):):):)

---

