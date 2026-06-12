---
title: "unnecessary password typing"
date: 2008-09-19
forum: General Help
---

### Post by Woody1987 on 2008-09-19
Whenever i want to connect to a remote computer through Remote Desktop Viewer or do a Send/Receive in Evolution i am prompted to type in my root password. Once entered i wont have to type it in again until i restart and the password works on both programs, i.e. if i type in my root password for evolution, RDV wont ask me for it, and vice versa, its as though im giving both programs root privilages at the same time for an unlimited time. 

It doesnt seem necessary that i should have to do it at all because im sure i didnt have to in the past and i cant remember anything i have done recently that would cause this to happen, such as changing permissions on a file or something. Any help appreciated.

---

### Post by Pro-reason on 2008-09-19
There shouldn't even be a root password on Ubuntu, let alone a root password you have to enter for e-mail.  It's difficult to ascertain what you have done to the system.

---

### Post by mb_webguy on 2008-09-20
Remote Desktop Viewer shouldn't require a password except that of the remote computer, and Evolution shouldn't require you to enter a password except when you first set up an account.

Check the launchers in the menu and see if the commands to launch the programs are preceded by gksu for some reason...

---

### Post by Woody1987 on 2008-09-20
> There shouldn't even be a root password on Ubuntu, let alone a root password you have to enter for e-mail. It's difficult to ascertain what you have done to the system.
by root password i mean my password i.e. the one i have to enter when i do a sudo command.

> Remote Desktop Viewer shouldn't require a password except that of the remote computer, and Evolution shouldn't require you to enter a password except when you first set up an account.

Check the launchers in the menu and see if the commands to launch the programs are preceded by gksu for some reason...
i realise that i shouldnt be entering a password. For your second point there are no proceeding commands such as gksu. The passwords only need to be entered when i click 'Connect' in remote desktop viewer and 'Send/Receive' in evolution not when i first load the program.

---

### Post by Woody1987 on 2008-09-21
bump

---

