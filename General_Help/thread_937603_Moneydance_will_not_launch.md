---
title: "Moneydance will not launch"
date: 2008-10-04
forum: General Help
---

### Post by wmjpalmerjr on 2008-10-04
Hello, Just switch to Ubuntu/Linus yesterday. Most everything is running great. I intalled Moneydance, but cant make it launch. Tried the "Moneydance" file in the ;'moneydance' folder, but no go.

Any help to be had, thanks wm

---

### Post by Peter09 on 2008-10-04
Try running it from a terminal, you may get more informative error messages.

Open a terminal Applications->Accessories->Terminal

at the prompt type moneydance, see what output you get. (how did you install it?)

---

### Post by wmjpalmerjr on 2008-10-04
Thanks,
Here is what happened

erjr@dell-desktop:~$ moneydance
bash: moneydance: command not found
wmjpalmerjr@dell-desktop:~$ 

ALSO: I installed through the terminal.

thanks again, wm

---

### Post by Peter09 on 2008-10-04
Hi,
go to the directory where the application is through the terminal and type in a terminal

```
./moneydance
```

see what happens then

---

### Post by wmjpalmerjr on 2008-10-05
Here is the output:

wmjpalmerjr@dell-desktop:~/moneydance$ moneydance
bash: moneydance: command not found
wmjpalmerjr@dell-desktop:~/moneydance$

Seems like I might have installed it incorrectly maybe.
The Windows version (over on the other machine) runs well.
BUT I am in the process to do away with Vista, and Moneydance is the last program I need/wnat working before making the "complete" split.

Oh Ya, thank you for you time and efforts, Wm

---

### Post by wmjpalmerjr on 2008-10-05
update,

Sunday I did a complete uninstall and install in shell.

No change, still will not start, getting the same error message, see previous post with information.

wm
:(

---

### Post by Peter09 on 2008-10-06
go to the moneydance directory in a terminal and type
```
ls
```

what files do you see?

---

### Post by cariboo on 2008-10-06
THe executeable for Moneydance is in /usr/local/bin to start the program in a terminal tyoe:

```
/usr/local/bin/Moneydance
```

To create a laucher right click on the desktop, click create launcher, type in the name in the name box, in the command box tpye the above command then clcik OK.

In the future just because a program doesn;t work the way you expect it to, reinstalling will not help the problem, 99% of the time you will get the same result as before you reinstalled. Remember Linux is not Windows, most of what you know about computers is of no use. 

Using Ubuntu is a learning experience. Most of what you learn using Ubuntu will make you a better computer user in the Windows world.

Jim

---

### Post by wmjpalmerjr on 2008-10-08
Hello again,

Using Launcher I got it to work.

Here is my shell activity:

wmjpalmerjr@dell-desktop:~$ cd moneydance
wmjpalmerjr@dell-desktop:~/moneydance$ ls
appsrc.jar          jfreechart-1.0.9.jar  Moneydance             moneydance.jar
error.log           jre                   Moneydance.desktop     uninstall
jcommon-1.0.12.jar  license.txt           moneydance_icon32.png
wmjpalmerjr@dell-desktop:~/moneydance$ Moneydance
bash: Moneydance: command not found
wmjpalmerjr@dell-desktop:~/moneydance$ 


As you can see, using the "Moneydance", as done in Launcher, failed to activate the program.

Thanks again, Wm

---

### Post by LineOf7s on 2008-10-08
> **wmjpalmerjr said:**
> Here is the output:

wmjpalmerjr@dell-desktop:~/moneydance$ moneydance
bash: moneydance: command not found
wmjpalmerjr@dell-desktop:~/moneydance$

Seems like I might have installed it incorrectly maybe.
The Windows version (over on the other machine) runs well.
BUT I am in the process to do away with Vista, and Moneydance is the last program I need/wnat working before making the "complete" split.

Oh Ya, thank you for you time and efforts, Wm

Almost right.  The post above advised you to start Moneydance with the command ```
./moneydance
``` once you'd changed to the correct directory.  **The . and the / are both required** or it will do as you've reported.

Try this again, but this time type **./moneydance** in that directory, and see what happens.

---

### Post by lrf on 2008-12-28
> **LineOf7s said:**
> Almost right.  The post above advised you to start Moneydance with the command ```
./moneydance
``` once you'd changed to the correct directory.  **The . and the / are both required** or it will do as you've reported.

Try this again, but this time type **./moneydance** in that directory, and see what happens.

This is what I've accomplished (launch did not work.):

linda@linda-desktop:~/Desktop/Linda/Downloads/tar/Moneydance$ ./Moneydance
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.4.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/linda/.install4j

I deleted install4j.  I suppose that I need to point to a suitable JVM. Please be kind enough to give example as how to point to JVM. See next lines for directories from extraction:

linda@linda-desktop:~/Desktop/Linda/Downloads/tar/Moneydance$ ls
appsrc.jar          jfreechart-1.0.9.jar  Moneydance   moneydance_icon32.png
jcommon-1.0.12.jar  license.txt           Moneydance~  moneydance.jar

Java

linda@linda-desktop:/usr/share/java-common$ ls
java-common.sh  jvm-find.sh


I think that what is being asked by pointing to JVM is to create a symbolic link. Hope the information above will assist you assisting me writing that link. Thanks.

---

