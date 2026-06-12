---
title: "Installation"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by sarvan.rb on 2009-02-23
Hi friends. I am a new user to ubuntu. I started to use this for bioinformatics. i need to install a software ARB (bioinformatics tool). i have read through the manual and instructions, about Add/Remove applications, synaptic package manager.... i am not able to figure out how to install and run the program. 

i followed the instructions to install. my problem is, i dont know whether it is installed or not. like in windows, if we install a software, there is a shortcut in start menu for that program, or we click the exe file in Program Files folder. similarly will there be any shortcut to open the installed files. Kindly help me as i should use this software for my project.

it would be great if anyone here provides me a step by step instruction about this. the software i am talking about could be found at [http://www.arb-home.de/downloads.html](http://www.arb-home.de/downloads.html) I even dont know which version of this to download (.sh, .tgz, )

---

### Post by oldos2er on 2009-02-23
According to their README, you would open a terminal and enter "arb".

---

### Post by sarvan.rb on 2009-02-23
I have installed the software.. but finally it says

Note for sysadmins:
     In order to provide arb for all users,
     edit the global shell init file(s) in /etc
     (/etc/bash.bashrc, /etc/csh.cshrc or similar)
     in the same manner as described above for the
     local shell init files.
 What should i do now?

---

### Post by sarvan.rb on 2009-02-23
Its given that i have to edit the init file and add d following line.

# bash users add to ~/.bashrc:
  alias arb=/home/bioinfo/Desktop/arb/bin/arb

how should i edit it now?

---

### Post by oldos2er on 2009-02-23
I think the file you need to edit is /etc/profile .

---

