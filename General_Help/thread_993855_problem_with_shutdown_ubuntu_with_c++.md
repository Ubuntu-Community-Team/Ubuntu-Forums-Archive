---
title: "problem with shutdown ubuntu with c++"
date: 2008-11-26
forum: General Help
---

### Post by ekansdiuqil on 2008-11-26
I want to shutdown my computer with a program that is opened with the 
Preference->Session. i.e I want my computer only works with my program
and when a key is pressed I call a function in my program(written with c++) and it processes the line:

system("sudo -u root -p password shutdown -h 0");

but it doesn't work. I tried to change the sudoers file as
%admin ALL=(ALL) ALL
%user ALL=(ALL) ALL
 it only works if I call the program from terminal and if sudo is used before i.e. if I entered somewhere the password before.

Is there any thing should to to process the above line ?

---

