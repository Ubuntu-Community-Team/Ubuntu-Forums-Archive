---
title: "Can't shut down ubuntu from IR remote"
date: 2008-10-15
forum: General Help
---

### Post by myth01 on 2008-10-15
I'm using a laptop as a mythtv frontend under my TV.  I'm trying to use an MCE USB IR remote to control it and have come across 2 problems...

1) It will launch mythtvfrontend when the 'Home' button is pushed, but it seems that logging fails when it is launched this way (new logs get created and contain incomplete information) which I am guessing is a problem with the user that the frontend is run as or something else related to the permissions, but I don't know enough about either of those subjects.

2) I can't get the remote to shutdown the laptop.  I've edited the sudoers so that /sbin/shutdown doesn't request a password, and tested it in the terminal and it works that way but I can't get the remote to trigger it.  The 'Power' button is set to lanuch a script containing 
```
sudo shutdown -h now
```
I tried to run the script from the terminal, but got
```
shutdownscript: command not found
```
the script is owned by 'server' and is executable so again I've hit a wall.

I'm fully expecting the answer to both problems to be painfully simple....but any help or pointers would be appreciated....

---

### Post by myth01 on 2008-10-15
...bump...

---

