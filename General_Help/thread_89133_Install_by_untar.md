---
title: "Install by untar"
date: 2005-11-11
forum: General Help
---

### Post by edross on 2005-11-11
I have a few programs (eclipse & dbvisualizer) that I downloaded and installed by simply un-tarring into a selected directroy.   Both are Java programs is that matters.

I'm running java 1.5

When I use the command line to run the programs, everything seems fine.  When I try and start the programs by double clicking on an icon, they don't seem to work.

I installed Java jdk1.5 by downloading it from sun and running the install as root.

I put java in /urs/local/java...
I modified the startup scripts basch  to put the java1.5 jdk as the first item in the path.

I;m thinking that gome sill is using the java 1.4 stuff, but don't know how to verify.

Any help would be appreciated.

thanks

ed

---

### Post by Joe_lurker on 2005-11-12
What command do you use to run the program from the command line?

-Joe

---

### Post by edross on 2005-11-12
from the command line I simply change to the directory and start the program.

example

cd /home/edross/eclipse
eclipse

is used to start eclipse.

---

### Post by Joe_lurker on 2005-11-12
I was able to start eclipse by double-clicking on the "eclipse" icon in the eclipse folder with using the file browser.  What happens when you do this?  To be clear what icons are you double-clicking on when it fails?

Since I have not installed any additional Java components I would guess it is not a version problem.

-Joe

---

### Post by edross on 2005-11-12
Hi Joe,

I modified bash.bashrc to put java 1.5 first in the path.  This works fine when I use a command window/ terminal.  However, when I execute from the browser, It is still using java 1.4

wrote this script

cd /home/edross/eclipse
java -version >temp.txt

when execute from a terminal window, java 1.5
when execute from a explorer window java 1.4

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


I just want to remove java 1.4 and install java 1.5, but even when I tell the packagemanger to remove it,  it says all is well, but 1.4 is still there.

thx for the reply

---

### Post by Joe_lurker on 2005-11-12
You shouldn't modify the /etc/bash.bashrc.  Modify your /home/<user>/.bashrc.  However this wont solve this problem, just a tip as it only runs when you open a terminal.

You can make your Java 1.5 the default by replacing the link in /usr/bin.
```
cd /usr/bin
ln -sf /path/to/java1.5/bin/java
```
Then you shouldn't have to mess around with the path.
Alternatavely you could create a launcher with the following options:
```
Name: Eclipse
Comment: Start Eclipse IDE
Command: /path/to/java1.5/bin/java -jar /home/edross/eclipse/startup.jar
```
I hope I helped more then confused.

EDIT: As I stated in a previos post Eclipse works for me with the default Java install.  But that's besides the point.

-Joe

---

### Post by amazongalhn on 2005-11-12
I loaded Sunjava 1.5 and the NetBeans IDE in a previous set up.   I recently reloaded my system and this time I am refraining from going directly to Sun for two reasons:

1)   I want to aquaint myself with the GNU version and for learning the basics of java this should be quite adaquit.

2)   The name (symbol) "java" is part of the alternatives system.   As such one must either be conversent with administering the alternatives system or track down the last symbolic link and rewrite it to point to the 1.5.  This is most likely why your launch isn't working.   There is an info or man page on the alternative system,  the purpose of which is to allow different version of similarly named apps to exist on the system and be referenced by different users.  I'm not really conversant with it.  By breaking into the link chain you effectively break the system for that particular name (symbol).

---

### Post by edross on 2005-11-12
Joe - first, eclipse with java 1.4 will fail in various and wierd ways - not only just on startup.  There is a know problem with linux and eclipse 3.1 using java 1.4  


I did what you suggested 

 sudo  ln -sf /usr/local/jdk1.5.0_05/bin/java java

and all works well.   Thanks a bunch.

---

