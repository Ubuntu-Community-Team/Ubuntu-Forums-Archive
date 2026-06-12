---
title: "Very Important command line problem"
date: 2008-08-27
forum: General Help
---

### Post by Greenbean209 on 2008-08-27
My problem is very bad. When ever I have to CD or use a program that refers to a file or to a directory, when i put in the name I always get a message that says no such file or directory. I know I have the name right so I have no Idea what could be happening. So until I can figure out what I'm doing wrong I can't do really anything with the command line. I have a few examples of what happens if it helps.


```

john@john-desktop:~$ sudo  mount -o loop diablo2playdisc.iso /media/iso
diablo2playdisc.iso: No such file or directory
john@john-desktop:~$ cd pictures
bash: cd: pictures: No such file or directory
john@john-desktop:~$ cd /home/john/pictures
bash: cd: /home/john/pictures: No such file or directory
john@john-desktop:~$ cd '/home/john/pictures'
bash: cd: /home/john/pictures: No such file or directory
john@john-desktop:~$ /home/john/pictures/
bash: cd: /home/john/pictures/: No such file or directory
john@john-desktop:~$
```

Im pretty sure I did it right so I have no idea what could be happening. Someone please correct me if I'm wrong.

---

### Post by sisco311 on 2008-08-27
use *pwd *to list the current/working directory.
and *ls *to list the files and folders.

Linux is case sensitive.

To find the full path to a file/folder just drag and drop it in the terminal. ;)

---

### Post by iaculallad on 2008-08-27
> **Greenbean209 said:**
> 
```

john@john-desktop:~$ sudo  mount -o loop diablo2playdisc.iso /media/iso
diablo2playdisc.iso: No such file or directory
john@john-desktop:~$ cd pictures
bash: cd: pictures: No such file or directory
john@john-desktop:~$ cd /home/john/pictures
bash: cd: /home/john/pictures: No such file or directory
john@john-desktop:~$ cd '/home/john/pictures'
bash: cd: /home/john/pictures: No such file or directory
john@john-desktop:~$ /home/john/pictures/
bash: cd: /home/john/pictures/: No such file or directory
john@john-desktop:~$
```

Im pretty sure I did it right so I have no idea what could be happening. Someone please correct me if I'm wrong.

Make sure that the ISO file you're trying to mount is in your Desktop. Remember that in Linux, everything is case-sensitive. Meaning, picture is not the same as Picture. So to correct your code, do:

```
cd ~/Pictures
cd /home/john/Pictures

```

---

### Post by rossdub on 2008-08-27
I agree with the two posters above...use ```
john@john-desktop:~$ls
``` and ```
john@john-desktop:~$pwd
```to make sure you are in the right directory and that the directory you are cd'ing to exists where you think it exists.  

Also, make sure you are using tab complete when cd'ing or doing any file operation (mv, cp, rm, etc.)  Basically, after you type a few letters of what you think is the correct file name, press the tab key and the filename or directory name is completed for you.  This really helps avoid spelling errors and 'No such file or directory' errors, as well as reducing the amount of text you have to type, especially if you have long filenames and/or complex folder structure.   

If nothing happens after pressing tab once, press it again and a list of all possible completions will be displayed.  You can continue from there.

If nothing is displayed or completed after pressing tab twice, there is no file or directory name in the current directory which begins with what you have already typed.  Change directories, use ls, pwd to make sure you are in the right spot.

---

