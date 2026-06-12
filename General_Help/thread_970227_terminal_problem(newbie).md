---
title: "terminal problem(newbie)"
date: 2008-11-04
forum: General Help
---

### Post by curr3ncychas3 on 2008-11-04
everytime i enter anything in the terminal and press enter, this comes up


myname@mycomputer:~$ sudo aptitude install opera
[sudo] password for myname: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
myname@mycomputer:~$


it comes up everytime i use the terminal to install anything.
can some one help me out

---

### Post by Ryadt on 2008-11-04
Do ```
sudo dpkg --configure -a
```

---

### Post by curr3ncychas3 on 2008-11-04
i entered the code 
sudo dpkg --configure -a

and then tried to install opera ,then this happened

myname@mycomputer:~$ sudo aptitude install opera
[sudo] password for myname: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for opera
No candidate version found for opera
The following packages have been kept back:
  sun-java6-jre 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch)
myname@mycomputer:~$

---

