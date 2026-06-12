---
title: "[SOLVED] Can't empty trash, permissions denied."
date: 2008-07-13
forum: General Help
---

### Post by rossjman1 on 2008-07-13
I have these two directories (which are copies of 2 data cds), and I don't have permission to delete them. This wouldn't normally be a problem, but I cant change the permissions in Nautilus (error message: Sorry, couldn't change the permissions of "sc4d1s": Operation not supported by backend), and these directories dont seem to exist in the terminal (see screenshot). The only two files (according to the terminal) are the standard . and ..
[IMG]http://img149.imageshack.us/img149/2801/screenshotjeffjefflaptohe5.png[/IMG]

---

### Post by sisco311 on 2008-07-13
the trash folder in Hary Heron(8.04) = ~/.local/share/Trash

---

### Post by jonlemur on 2008-07-13
See if [this thread]("http://ubuntuforums.org/showthread.php?t=856837&highlight=trash") helps.

---

### Post by tunznath on 2008-07-13
or this one - worked for me
[http://ubuntuforums.org/showthread.php?t=827226](http://ubuntuforums.org/showthread.php?t=827226)

---

### Post by rossjman1 on 2008-07-13
thanks, sudo rm -r sc4d1 did the trick

---

### Post by darkazurka on 2009-05-21
.local/share/Trash has two subfolders: **files** and **info**. When your trash is successfully deleted both those folders are empty.

If you want your trash just to seem empty delete all files in the subfolder **files** .

---

