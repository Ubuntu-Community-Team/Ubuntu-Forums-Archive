---
title: "Terminal Will Not Open."
date: 2008-08-08
forum: General Help
---

### Post by Newuser1111 on 2008-08-08
Terminal(gnome-terminal) will not open.

---

### Post by Ryadt on 2008-08-08
Did you try ALT+F2 > Gnome-terminal?

---

### Post by Newuser1111 on 2008-08-08
> **Ryadt said:**
> Did you try ALT+F2 > Gnome-terminal?Yes.
It still doesn't open.

---

### Post by Ryadt on 2008-08-08
Sorry do u mean that it doesnt open at all or does it crash just after opening?

---

### Post by dje on 2008-08-08
please press Alt + F2 and run:
```
xterm
```
then try and run:
```
gnome-terminal
```
from the xterm, please post the output here

dje

---

### Post by Newuser1111 on 2008-08-08
> **dje said:**
> please press Alt + F2 and run:
```
xterm
```
then try and run:
```
gnome-terminal
```
from the xterm, please post the output here

dje
No output,
```
djk@djk-laptop:~$ gnome-terminal
djk@djk-laptop:~$ 
```

---

### Post by Ryadt on 2008-08-08
> **Newuser1111 said:**
> No output,
```
djk@djk-laptop:~$ gnome-terminal
djk@djk-laptop:~$ 
```

Sorry....but looks like your terminal is open....

---

### Post by dje on 2008-08-08
strange...
try:
```
sudo apt-get autoremove --purge --reinstall gnome-terminal
```

dje

---

### Post by dje on 2008-08-08
> **Ryadt said:**
> Sorry....but looks like your terminal is open....

xterm not gnome-terminal..

---

### Post by Newuser1111 on 2008-08-08
> **dje said:**
> strange...
try:
```
sudo apt-get autoremove --purge --reinstall gnome-terminal
```

djeNow when I run "gnome-terminal" in xterm it says
```
bash: /usr/bin/gnome-terminal: No such file or directory
```

---

### Post by dje on 2008-08-08
> **Newuser1111 said:**
> Now when I run "gnome-terminal" in xterm it says
```
bash: /usr/bin/gnome-terminal: No such file or directory
```

ok it musn't have reinstalled it:
```
sudo apt-get install gnome-terminal
```

dje

---

### Post by Newuser1111 on 2008-08-08
> **dje said:**
> ok it musn't have reinstalled it:
```
sudo apt-get install gnome-terminal
```

djeNow "gnome-terminal" still doesn't open.
xterm shows no output.

---

### Post by tjwoosta on 2008-08-08
wtf...


just to be sure it installed correctly go to System-Administration-Synaptic Package Manager and search for **gnome-terminal**  if it is not marked then mark it for installation  (also you will need to make sure **gnome-terminal-data** is also installed)

if both of theese are already installed then try reinstalling again

if that dont work then theres something really strange going on

---

### Post by Newuser1111 on 2008-08-08
> **tjwoosta said:**
> wtf...


just to be sure it installed correctly go to System-Administration-Synaptic Package Manager and search for **gnome-terminal**  if it is not marked then mark it for installation  (also you will need to make sure **gnome-terminal-data** is also installed)

if both of theese are already installed then try reinstalling again

if that dont work then theres something really strange going onBoth gnome-terminal and gnome-terminal-data are installed.

Reinstalled them again, and it still doesn't work.

---

### Post by dje on 2008-08-08
this so strange :confused:
try creating a new user account and seeing if gnome terminal opens in that account

dje

---

### Post by Newuser1111 on 2008-08-08
> **dje said:**
> this so strange :confused:
try creating a new user account and seeing if gnome terminal opens in that account

djeIt works, on the new user account.

---

### Post by dje on 2008-08-08
ok log back into your original user and execute the following from xterm:
```
cp -r $HOME/.gconf/apps/gnome-terminal $HOME/gnome-terminal-backup
rm -r $HOME/.gconf/apps/gnome-terminal
```
this backs up the gnome terminal settings folder and then deletes it, then try starting it again

dje

---

### Post by Newuser1111 on 2008-08-08
> **dje said:**
> ok log back into your original user and execute the following from xterm:
```
cp -r $HOME/.gconf/apps/gnome-terminal $HOME/gnome-terminal-backup
rm -r $HOME/.gconf/apps/gnome-terminal
```
this backs up the gnome terminal settings folder and then deletes it, then try starting it again

djeThere was a problem with the first one.(So I didn't even do the second one)
```
cp: cannot stat '/home/djk/.gconf/apps/gnome-terminal': No such file or directory
```

---

### Post by dje on 2008-08-08
ok try:
```
mkdir $HOME/.gconf/apps/gnome-terminal
mkdir $HOME/.gconf/apps/gnome-terminal/profiles
mkdir $HOME/.gconf/apps/gnome-terminal/profiles/Default
touch $HOME/.gconf/apps/gnome-terminal/%gconf.xml
touch $HOME/.gconf/apps/gnome-terminal/profiles/%gconf.xml
touch $HOME/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml
```
and try starting gnome terminal again

dje

---

### Post by Newuser1111 on 2008-08-08
> **dje said:**
> ok try:
```
mkdir $HOME/.gconf/apps/gnome-terminal
mkdir $HOME/.gconf/apps/gnome-terminal/profiles
mkdir $HOME/.gconf/apps/gnome-terminal/profiles/Default
touch $HOME/.gconf/apps/gnome-terminal/%gconf.xml
touch $HOME/.gconf/apps/gnome-terminal/profiles/%gconf.xml
touch $HOME/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml
```
and try starting gnome terminal again

djeIt still doesn't work.

---

### Post by dje on 2008-08-08
Well i'm all out of ideas, you could either use a different terminal (such as xfce4-terminal or xterm) or transfer your files to the new user and use that user

sorry i can't be of any more help,
dje

---

### Post by Newuser1111 on 2008-08-08
Does anyone else have any ideas?

---

### Post by dje on 2008-08-08
for now i'd suggest just trying xfce4-terminal:
```
sudo apt-get install xfce4-terminal
```
it offers the same features and looks pretty much the same too

dje

---

### Post by Newuser1111 on 2008-08-08
> **dje said:**
> for now i'd suggest just trying xfce4-terminal:
```
sudo apt-get install xfce4-terminal
```
it offers the same features and looks pretty much the same too

djeIt's close enough. 
(As long as it allows Copy/Paste)

---

