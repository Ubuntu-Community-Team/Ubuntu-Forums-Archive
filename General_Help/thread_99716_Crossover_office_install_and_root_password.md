---
title: "Crossover office install and root password"
date: 2005-12-06
forum: General Help
---

### Post by will103 on 2005-12-06
Hi,

I have been trying to install crossover office 5 and have encountered a small problem. I would like to install it so that all users on my system can install and use office 2003 (I like Open Office personally, but some of my other users want to use Office 2003 for their work). I tried to install crossover office using the sudo command but the script exits to the shell, informing me that I should login as root to install. 

How risky is it to enable root? Reading around some of the Ubuntu documentation, I get the impression that doing so might break some of the administrative tools. Also, has anyone managed to install crossover office for mutliple users without using the root account?

Thanks in advance for your help.

WIll103

---

### Post by hw-tph on 2005-12-06
For the purpose of installing the software, try **sudo bash**. That would give you a root shell (you can verify that with the **whoami** command). When done installing, simply press Ctrl+D (end of file) or **exit** to exit the root shell.


H&#229;kan

---

### Post by will103 on 2005-12-06
[QUOTE=hw-tph]For the purpose of installing the software, try **sudo bash**. That would give you a root shell (you can verify that with the **whoami** command). When done installing, simply press Ctrl+D (end of file) or **exit** to exit the root shell.


Håkan[/QUOTE]

Thanks Håkan.

Will103

---

### Post by Hezekiah on 2005-12-06
Also, I believe:
```
sudo -s
```
should do what you need.

---

