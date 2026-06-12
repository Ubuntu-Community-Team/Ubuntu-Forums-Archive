---
title: "Need help to delete Desktop.ini"
date: 2008-08-19
forum: General Help
---

### Post by mxlaser on 2008-08-19
Hi, i have folders within folders in my trash
and in them, they have desktop.ini
I can not delete them by clicking "Empty Trash"
please and thank

---

### Post by colobix on 2008-08-19
you have to do it as administrator.

gksudo nautilus, then browse for the file.

---

### Post by mxlaser on 2008-08-19
wont let me go into trash bin 

it said,  "Sorry, couldn't display all the contents of "trash": Operation not supported"

---

### Post by colobix on 2008-08-19
I guess u have to login as root then (Shell)
Sudo su
username root
password should be passwd.
BUt do NOT mess around with things u don't know where is going then.
Delete the .ini file and that's it.

---

### Post by mxlaser on 2008-08-20
um.. i am very new to ubuntu, can you tell me what to type? 
i got to the part were i input my password but got lost after that

---

### Post by kerry_s on 2008-08-20
open nautilus, press ctrl+h, delete the folder ".Trash"
when i say delete, edit> preferences> behavior, make sure the "include a Delete command that bypasses the Trash" is selected.

---

### Post by mxlaser on 2008-08-21
um the folder is not .trash, the folder is in the recycle bin 
and when nautilus is opened, it won't let me go into the recycle bin
and i changed it to by pass trash and it still wont delete from my recycle bin :(

---

### Post by jerome1232 on 2008-08-21
first of all root login is disabled in ubuntu so sudo su will not work.

second of all runing nautilus as root isn't advised.

lets do it this way: open a new terminal window
```
cd .local/share/Trash/files
sudo ls -a           # this should list out the files, if it looks like what you want to delete then go ahead and remove them
sudo rm *
```


EDIT: BE VERY CAREFUL WITH SUDO RM * IT REMOVES ALL FILES IN CURRENT DIRECTORY, so if you aren't in the write spot, it will wipe all files in the current directory, the only thing more dangerous is sudo rm -r and sudo rm -rf, never run those unless you know why you would want to in a certain instance

---

### Post by mxlaser on 2008-08-25
> 
lets do it this way: open a new terminal window
```
cd .local/share/Trash/files
sudo ls -a           # this should list out the files, if it looks like what you want to delete then go ahead and remove them
sudo rm *
```


what do i put in after sudo rm? 

```

~/.local/share/Trash/files$ sudo ls -a
.  ..  untitled folder1

```

after this i dont know what to put

```

~/.local/share/Trash/files$ sudo rm untitled folder1
rm: cannot remove `untitled': No such file or directory
rm: cannot remove `folder1': No such file or directory
~/.local/share/Trash/files$ sudo rm .  ..  untitled folder1
rm: cannot remove directory `.'
rm: cannot remove directory `..'
rm: cannot remove `untitled': No such file or directory
rm: cannot remove `folder1': No such file or directory

```

---

### Post by jerome1232 on 2008-08-25
okay those look like directories
```
sudo rm -rf ~/local/share/Trash/
```

---

### Post by mxlaser on 2008-08-31
it doesnt work.. i type that but nothing happens -.-

---

