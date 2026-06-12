---
title: "How create script for start a program?"
date: 2008-09-23
forum: General Help
---

### Post by gaiterin on 2008-09-23
Hi!
I'm developer of Gufw.
I was testing in Kubuntu 8.10 and not runs, because I try run with "gksudo..." and not exist.
I need start not Gufw, I need start a script, and if the session is:
Gnome: gksudo --preserve-env --desc.......... gufw.py
KDE:   kdesu ..........gufw.py
Can you help me, please?
Thanks a lot!
Marcos.

---

### Post by qstraza on 2008-09-23
What? :P

---

### Post by gaiterin on 2008-09-23
I need this script:
If gnome session:
    command: gksudo gufw
if kde session:
    command: kdesu gufw

---

### Post by qstraza on 2008-09-23
well login to KDE and paste output of "ps x"
Than login to GNOME and paste output of "ps x"

And i will write you a script ;)

---

### Post by gaiterin on 2008-09-23
Why do you need the exit?
Thanks.

---

### Post by qstraza on 2008-09-23
I need to see whats different under proccesses, whats uniq in kde and what in gnome, i dont have gnome, so i dont know what is

---

### Post by Leslie Viljoen on 2008-09-23
I think the OP may be asking for the correct standard way to start a program as root whether on Gnome or KDE. Surely quite a few programs need to do this, so how is it done?

---

### Post by qstraza on 2008-09-23
well im not sure what he wants, but i understand as he wants one script which will check if he is currently in gnome and do something (eg gksudo) or if it is in kde ...

---

### Post by gaiterin on 2008-09-23
I need run a python program as graphical sudo.
But in kde not exist gksudo.
I need when the session is kde or gnome.

---

### Post by qstraza on 2008-09-23
well get me that ps x of both sessions, as i said before

---

### Post by qstraza on 2008-09-23
well try this```

#!/bin/bash

cmd=`ps x | grep kdeinit`

if [ ${#cmd} -gt 50 ]; then
    echo kde
else
    echo gnome
fi

``` 

but till i see "ps x" from both, it aint sure;>

---

### Post by gaiterin on 2008-09-24
Hi!
I try with this.
Is a good script?

```
#!/bin/bash
#This script checks if the window manager uses gksudo or kdesudo
gnome=`which gksudo`
kde=`which kdesudo`

#Run command
if [ -n "$gnome" ]; then
	echo "Gnome!"
elif [ -n "$kde" ]; then
	echo "KDE!"
else
	echo "OTHER!"
fi

```

---

### Post by qstraza on 2008-09-24
if u have both KDE and GNOME on 1 PC, this script will not work.

---

### Post by gaiterin on 2008-09-24
If I have "gksudo" installed in kde is sufficent, I need only know how run the application (with gksudo/kdesudo/sudo).

---

### Post by qstraza on 2008-09-24
gksudo is installed on PC not in GNOME, so nomatter in which X manager you are, there will always be gksudo, that ofcourse if you have ubuntu and some other X manager.

---

