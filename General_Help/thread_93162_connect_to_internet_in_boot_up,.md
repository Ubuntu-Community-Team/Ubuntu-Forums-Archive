---
title: "connect to internet in boot up,"
date: 2005-11-21
forum: General Help
---

### Post by yhotg on 2005-11-21
hi again.

i want kubuntu to login to my internet connection in boot up.
i connect by typing in a console :

# sudo internet --connect=<connection-name>
#password:*******

and i want kubuntu to desconnect my internet connection when loging off the system

the command i use for closing my internet connection is:

#sudo internet --clearcurr
#password:*************

so how i write a script or something so the internet connection gets up in boot up and gets down when closing the computer?

thanks

---

### Post by blastus on 2005-11-21
To run an application or command on startup, create a bash script in the ~/.kde/Autostart directory. For example...

#!/bin/sh
kwrite &

...would open kwrite on startup (you need to give the script execute permissions with "chmod +x") You don't need the ampersand "&" if you are just running a terminal command. However, I'm not sure about using sudo in a bash script and I don't know how to run a command upon logout.

---

### Post by yhotg on 2005-11-22
ok, 
now, any idea where i can learn to write scripts?

:)
:o

---

