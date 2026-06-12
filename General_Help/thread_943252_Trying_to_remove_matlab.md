---
title: "Trying to remove matlab"
date: 2008-10-10
forum: General Help
---

### Post by Jacob Collstrup on 2008-10-10
Heya,

I'm trying to ensure that matlab2007b is completely remove from my system before I reinstall. according to my teacher the problems I face during install is because its not completely out of the system yet.

So far I've managed to remove the /home/jacob/matlab2007b folder and the /home/jacob/.matlab folder.

I don't really remember which commands I used. But I need to totally remove everything labelled matlab before I try reinstall again.

How do I do that?

Jacob

---

### Post by Thanoulis on 2008-10-10
Try this:
```
sudo updatedb
```
and this:
```
locate matlab | more
```

Then remove the located files.

---

### Post by Jacob Collstrup on 2008-10-10
Thanks,

I managed to locate a few more files and folders.

I can't seem to delete this one:
/usr/local/matlab2007b

I tried marking it and press [SHIFT]+[DELETE], that didn't work...

I tried this in the terminal:
sudo rm ~/usr/local/matlab2007b

and it returned this error message:
rm: cannot remove `/home/jacob/usr/local/matlab2007b': No such file or directory


I figure its because It says 'jacob@jacob-laptop:~$' in the terminal, the terminal seems to be 'rooted' in /home/jacob/

Jacob

---

### Post by happyhamster on 2008-10-10
- Try:

sudo rm /usr/local/matlab2007b

- without the ~ character: that character expands to "/home/your_username/".

- A graphical way is starting nautilus as root:

gksudo nautilus

- You can then use nautilus to navigate to the file/folder and should be able to delete it. Don't forget to close nautilus afterwards (don't keep running it as root).

Good luck.

---

### Post by anal_paul on 2011-11-09
first find out your matlab folder, maximum time it will be in /usr/local folder
then
from cmd promt
type
>cd /usr/local
>sudo rm -r matlab
> enter your password


finish

---

