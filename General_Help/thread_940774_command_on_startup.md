---
title: "command on startup"
date: 2008-10-07
forum: General Help
---

### Post by vaazu on 2008-10-07
Hello,

I have to insert this line to the terminal "export LC_NUMERIC=en_US" every time I want to run a certain program. Where do I have to put it to make it automatic on startup, so I wouldnt have to enter it every time I want to run the program?

---

### Post by jerome1232 on 2008-10-07
Well the first way that comes to my mind is create a launcher script
pop open you favourite text editor
```

#!/bin/bash
# my app launcher
export LC_NUMERIC=en_US
/path/to/the/programs/executable
```
save it, (I'll pretend it's saved as 'applauncher'
```
chmod +x applauncher
```

For now on use that script to launch the app. You can make a menu entry or an icon on your panel if you wish.

---

### Post by vaazu on 2008-10-08
The problem is, I have to start the program in terminal like this ´"./nameofprogram filename" so this applauncher will not help me in this form.
Has someone got different proposals?

---

### Post by mixmaster on 2008-10-08
You could export this in the startup file for your shell.  If you are using bash this could be ~/.profile, ~/.bash_profile, ~/.bash_login or ~/.bashrc depending exactly on how you start your terminal and shell.

Alternatively, you could create the applauncher script like this:

#!/bin/bash
export LC_NUMERIC=en_US
/path/to/the/programs/executable $1

(note the similarity to the previous example).

This will pass the first parameter into the shell script and you can then do
applauncher filename (assuming applauncher is on your path).

---

