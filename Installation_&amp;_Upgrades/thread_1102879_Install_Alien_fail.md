---
title: "Install Alien fail"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by yossi59 on 2009-03-22
Hi
I am a new Linux/Ubuntu user
I have installed Ubuntu 8.04 LTS and want to use the alien command.
The system did not recognize the command.
I tried to install it and didn't succeed.
Below is the terminal output:

yossi@yossi-desktop:~$ sudo aptitude install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "alien"
Couldn't find any package whose name or description matched "alien"
The following packages have been kept back:
  ssl-cert 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
yossi@yossi-desktop:~$ 
yossi@yossi-desktop:~$ 

Yossi59

---

### Post by yossi59 on 2009-03-22
Hi
I am a new Linux/Ubuntu user
I have installed Ubuntu 8.04 LTS and want to use the alien command.
The system did not recognize the command.
I tried to install it and didn't succeed.
Below is the terminal output:

yossi@yossi-desktop:~$ sudo aptitude install alien
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initializing package states... Done
Building tag database... Done 
Couldn't find any package whose name or description matched "alien"
Couldn't find any package whose name or description matched "alien"
The following packages have been kept back:
ssl-cert 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initializing package states... Done
Building tag database... Done 
yossi@yossi-desktop:~$ 
yossi@yossi-desktop:~$ 

Yossi59

---

### Post by taurus on 2009-03-22
Post your /etc/apt/sources.list

```
cat /etc/apt/sources.list
```

[http://packages.ubuntu.com/hardy/alien](http://packages.ubuntu.com/hardy/alien)

---

### Post by Rocket2DMn on 2009-03-22
Threads merged - please do not create multiple threads on the same topic.  Thank you.

---

