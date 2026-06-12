---
title: "[SOLVED] Script?"
date: 2008-07-11
forum: General Help
---

### Post by Powerman2442 on 2008-07-11
Is there a way to make a script or a shortcut that will automatically open up a root terminal and run a program. For example open root terminal, not have to type in a password (or have to... it doesn't matter), and run chkrootkit (or any program for that matter.

Thanks,
Powerman2442

---

### Post by dcstar on 2008-07-11
> **Powerman2442 said:**
> Is there a way to make a script or a shortcut that will automatically open up a root terminal and run a program. For example open root terminal, not have to type in a password (or have to... it doesn't matter), and run chkrootkit (or any program for that matter.


You mean like cron jobs?

---

### Post by Powerman2442 on 2008-07-12
> **dcstar said:**
> You mean like cron jobs?

Not sure what that is or what you'd refer to a "script" as within Ubuntu/Linux. Basically I want to make a file, similar to a shortcut (or launcher) that I can name (and maybe put an image with) that automatically opens up root terminal, makes me type a password, but after doing that it automatically types in "chkrootkit" or "clamtk" so I don't need to open a root terminal (or terminal) and type in "chkrootkit" or "clamtk" (or gksudo <name>).

Just trying to save myself a step or two and figure out some basic "scripting" within Ubuntu. I will look up cron jobs though. To see if I can figure out what they are and if that is what I am looking for.

Thanks,
Powerman2442

---

### Post by chris4585 on 2008-07-12
create a launcher with a command like: gksudo <program>

this what you mean?

sorry didnt see the last post

---

### Post by jonlemur on 2008-07-12
If you right click on the desktop or in a panel you should get a "Create launcher" option.  In there you should find a Type dialog that lets you select "Application in terminal"  Then you can put in your command, like "sudo chkrootkit" and add an image by clicking on the icon in the top left.

---

### Post by Powerman2442 on 2008-07-12
> **chris4585 said:**
> create a launcher with a command like: gksudo <program>

this what you mean?

sorry didnt see the last post

Yes, that is pretty much what I was looking for. Thanks a bunch. I guess I could edit the original launcher so it does what I want it to. Never really thought of it.

Thanks again,
Powerman2442

---

### Post by jonlemur on 2008-07-12
You can also run your own scripts in this way.  For instance, if you have a directory in your home folder called scripts, and you had a file there called myScript.sh, you could put /home/USERNAME/scripts/myScript.sh in the Command section to run it.

---

### Post by Powerman2442 on 2008-07-12
> **jonlemur said:**
> You can also run your own scripts in this way.  For instance, if you have a directory in your home folder called scripts, and you had a file there called myScript.sh, you could put /home/USERNAME/scripts/myScript.sh in the Command section to run it.

How do you make a script for Ubuntu/Linux to do certain operations. Like...

launch terminal
stop
gksudo clamtk
stop
<type in password>

Something similar to this. And what program would I write the "script" under? gedit?

---

### Post by jonlemur on 2008-07-12
gedit is a good program to write them in, but you can use any text editor.  To do something like run a program from a terminal, maybe create a file containing a list of all the files in your home directory, sort them by the amount of space they take, and output that to the screen, you could do something like the following.

In gedit, ```
cd /home/jcarmicheal/
du -K | sort -n > tmp.txt
cat tmp.txt
rm tmp.txt
```

That could also easily be reduced in size, but this shows a little bit more of what can be done in a script.  Save this file as scriptname.sh and run it with ./scriptname.sh when you're in its directory.

---

### Post by jonlemur on 2008-07-12
You can also easily run any program like this.  For instance, in myscript.sh ```
gksu nautilus
``` will run nautilus in root mode after asking for a password.  Once you have the file saved, you can run it from an application launcher in a terminal like I posted above.

EDIT:  Here's a [website]("http://www.arachnoid.com/linux/shell_programming.html") that seems to have some good information on shell scripting

---

### Post by Powerman2442 on 2008-07-12
jonlemur - Thanks this is more of what I was looking for. Hoping it may eventually help me build up use of scripting within Ubuntu for more powerful ideas in the future. You never know... Thanks again, to everyone.

---

