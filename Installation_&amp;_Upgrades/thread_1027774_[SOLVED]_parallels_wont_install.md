---
title: "[SOLVED] parallels wont install"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by thingy87654321 on 2009-01-01
i am trying to install parallels but i get a error message when i run the ./install-sh command like it says in the instructions here is the error with the rest there

chris@chris-laptop:~$ cd /home/chris/parallels-2.2.2222-lin
chris@chris-laptop:~/parallels-2.2.2222-lin$ ./install.sh
Error: you must be root to run this script
chris@chris-laptop:~/parallels-2.2.2222-lin$ su ./install.sh
Unknown id: ./install.sh
chris@chris-laptop:~/parallels-2.2.2222-lin$ 



if you are wondering why the instructions say to extract using the command and the command is not in the message above, that is because i rather extract using a graphical interface instead of the terminal

here is the instructions i am using

      Locate file Parallels-2.2.xxxx-lin.tgz and extract it into any existing
      directory:
tar -xzpf Parallels-2.2.xxxx-lin.tgz -C <directory name>
      Go to the directory where you unpacked the .tgz file and issue the next command:
cd parallels-2.2.xxxx-lin
      Run the following command
./install.sh
6 After the installation completes, run the post-installation script. Issue the following
   command:


./install-sh does not work, any ideas on how to get it to work?

---

### Post by redneckProgrammer on 2009-01-02
Instead of *su ./install.sh*

try *[COLOR="Red"]sudo [/COLOR]./install.sh*

I believe the su command is to switch user, while the sudo command is used to execute a command as root.    If you want a little more info about these commands, try typing "man su"  or "man sudo" in a terminal.

---

### Post by bradthewanderer on 2009-01-02
Why not try something free such as Virtualbox?

---

### Post by thingy87654321 on 2009-01-02
i dont want virtual box, i already bought the keycode for parallels

---

### Post by thingy87654321 on 2009-01-02
after i install parallels i checked in synaptic because i was going to try uninstalling parallels and reinstalling it and when i clicked on the check box on the list it said "update" i clicked update and applyed changes and it worked, thanks for the help.
aka "sudo ./install-sh" worked, thanks again

---

