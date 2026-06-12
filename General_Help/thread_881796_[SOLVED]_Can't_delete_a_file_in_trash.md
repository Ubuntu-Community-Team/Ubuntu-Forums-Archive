---
title: "[SOLVED] Can't delete a file in trash"
date: 2008-08-06
forum: General Help
---

### Post by PhaeZee5 on 2008-08-06
There is a folder in my trash can that i can't delete because when I try, it says ```
Error removing file: Directory not empty
```.

When I try to move it to another folder, such as my desktop, it says the same thing, and does not move the folder.

I believe this is a 100% UNIX problem, so it isn't distro-specific, right?

---

### Post by tuxxy on 2008-08-06
You could try removing everythin in trash friom the command line, if you are certain you want to delete you could try

```
rm -rf ~/.Trash/*
```

Becareful and make sure the apth is correct before executing.

---

### Post by jonian_g on 2008-08-06
Open a terminal and type:

```
sudo nautilus /home/[your username]/.local/share/Trash/files
```

Right click on the files you want to delete and delete them.

---

### Post by Vivaldi Gloria on 2008-08-06
> **tuxxy said:**
> You could try removing everythin in trash friom the command line, if you are certain you want to delete you could try

```
rm -rf ~/.Trash/*
```

Becareful and make sure the apth is correct before executing.

The trash is in

```
/home/<your_username>/.local/share/Trash
```

now.

---

### Post by Vivaldi Gloria on 2008-08-06
> **jonian_g said:**
> Open a terminal and type:

```
sudo nautilus /home/[your username]/.local/share/Trash/files
```

Right click on the files you want to delete and delete them.

It's better to use gksudo with graphical applications:

```
gksudo nautilus /home/[your username]/.local/share/Trash/files
```

---

### Post by PhaeZee5 on 2008-08-06
Thanks for all the help! I followed jonian_g's advice, and it got rid of it.:)

---

