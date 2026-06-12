---
title: "Total noob question......."
date: 2008-07-19
forum: General Help
---

### Post by SARMedic on 2008-07-19
Hi all,
After fighting with Vista too much, Microsoft finally gave me enough initiative to finally install Linux (Ubuntu 8.04) yesterday. I've been playing around with Terminal, and for the life of me, can't figure out how to change the directory to a CD... 

C:\WINDOWS\> cd D:

I've tried everything I can think of, and I've been searching online for an answer, but can't turn one up. Problem is, I'm probably stuck in "windows mode" and am having a hard time thinking outside the box so to speak. 

Any help greatly appriciated!
Thanks,
Curtis

Edit: Another question... i was playing around with cd command, and got something like this...

curtis@curtis:~$ cd D:
No such file/directory...........
curtis@curtis:~$ cd D:\
etc...
curtis@curtis:~$ cd *bash head off keyboard*
>cd ..
>cd .
>cd curtis
>exit
>format everything
>help
>cd /?
>

why all the ">"?? did it go into some sort of different mode??

---

### Post by spiderbatdad on 2008-07-19
do you mean cd into the cdrom from a terminal?

```
cd /media/cdrom0
```

---

### Post by SARMedic on 2008-07-19
Perfect! Thanks!

---

### Post by mike2357 on 2008-07-19
You're almost there.

Windows systems map disk space to a drive letter, but Unix/Linux systems do not.

For instance to change directories to your "home" directory, you would execute the command:
cd /home/your_user_name

To change directories to where many of the programs live:
cd /usr/bin

The root directory:
cd /

You can also use your desktop interface and click on icons much as you do in Windows.

The next time you're at your local bookstore, you might buy a Unix or Linux book.  The command line in Linux is very powerful and is loaded with utilities.  Just take it a step at a time.

Good luck!

---

### Post by fragos on 2008-07-19
In Linux folder names are assigned to disk partitions and are referred to in applications as folders in one virtual disk. The default install would have created a a partition known as "/" which contains all data. Within that each user has a folder in "/home/{user name}. Why are you trying to set C:, logicaly Microsoft "C:" is Linux "/"?

---

