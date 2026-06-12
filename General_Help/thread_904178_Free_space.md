---
title: "Free space"
date: 2008-08-29
forum: General Help
---

### Post by sam_delta on 2008-08-29
hello

Yesterday i did a backup of my home partition and saved my bakup.tar into my filesystem "/". later on i copyied my backup file into my external drive and deleted the backup file from my filesystem. but now my filesystem is 80%full (as if i never deleted the 8gb backup file i had in there), i searched everywhere and could not find why it is reporting that much, if i right click it and click on properties, it reports a total of 15.1gb and a freespace of 2 gb (which is not possible, i dont have that much data on my fillesystem ( i have my data on my home partition)


if anyone is able to help, ill apreciate it
thanks 
sam

---

### Post by Elfy on 2008-08-29
How did you delete the backup tar? Check root's trash - [/CODE]gksudo nautilus[/code]

Root's trash is in /home/user/.Trash-0 iirc

---

### Post by sam_delta on 2008-08-29
hey, thanks for your reply, i bet the problem has something to do with trash

i deleted it by right clicking it and selecting the option "move to trash" (using a root nautilus), BUT could never find the file in the trash. so i thing its lost out there

also, i followed your previous post, but i couldnt find /home/user/.Trash-0, not even with a root nautilus, am i doing something wrong?

thanks
sam

---

### Post by sam_delta on 2008-08-29
ok i found the files under /root/.local/share/Trash/files

but somethins strange happens, when i try to delete them, they appear again in there (deleting the files moves them to trash again) lol
is there a way to force delte em?

thanks
sam

---

### Post by mocoloco on 2008-08-29
If you're using the gui, try shift+delete.  From command line rm should definitely get rid of them.

---

### Post by Elfy on 2008-08-29
This will do it from the cli - 

```
sudo rm -R ~/root/.local/share/Trash/files/*
```

---

### Post by sam_delta on 2008-08-29
alright, i did it, thanks for your help guys

you can always learn more things in ubuntu :)


sam

---

### Post by PGScooter on 2008-08-29
by the way, there is a really cool utility for finding out where all of your hard drive space is being eaten up:
filelight
Check it out, I really like it.

---

### Post by mocoloco on 2008-08-29
I like the included Disk Usage Analyzer (Applications -> Accessories), comes as default and no KDE dependencies.

---

### Post by sam_delta on 2008-08-30
yeah, i use the default Disk Analyzer, but ill take a look at filelight, remember, its free software!!!

sam

---

