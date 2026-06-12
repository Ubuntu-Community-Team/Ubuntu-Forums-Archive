---
title: "newbie Install updates problem"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Obeide on 2009-10-04
Hi, my laptop is coming up with the following error message when I try to install updates.  

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can someone please explain in layman's terms what I am supposed to do?

Thanks

---

### Post by Partyboi2 on 2009-10-04
Hi, open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
```

---

### Post by Obeide on 2009-10-04
thank you all sorted :)

---

### Post by ecksesnohhz on 2009-10-31
I keep getting the same message and I type in the command, then my password and nothing happens
 > samantha@Sammie:~$ sudo dpkg --configure -a
[sudo] password for samantha: 
samantha@Sammie:~$ sudo dpkg --configure -a
samantha@Sammie:~$ sudo dpkg --configure -a
samantha@Sammie:~$ 


---

### Post by Partyboi2 on 2009-10-31
> I keep getting the same message and I type in the command, then my password and nothing happens
  	Quote:
 	 	 		 			 				samantha@Sammie:~$ sudo dpkg --configure -a
[sudo] password for samantha: 
samantha@Sammie:~$ sudo dpkg --configure -a
samantha@Sammie:~$ sudo dpkg --configure -a
samantha@Sammie:~$  			 		



Can you now install updates?

---

