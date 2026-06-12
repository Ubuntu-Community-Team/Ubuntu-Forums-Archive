---
title: "Initial Installtion Problem (Wubi - Ubuntu 8.10)"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by Max Avion on 2009-05-08
Hello,

I had been running Wubi using an installation of Ubuntu 8.10 on my laptop running Windows XP Home Edition. That laptop recently crashed and I am trying to do the same thing on my new one but am having some problems. The laptop that I am using now has Windows Vista Business on the main hard drive and Windows XP Profession on a 16GB partition. I had installed Wubi using the same CD (ISO Image) that I used on the old laptop. The installation completed and the computer needed a re-boot. Once re-booting into Ubuntu the installation files extracted and then showed installation complete 100% after which the screen went black with just the cursor blinking, I think this also happened with the first installation. I re-booted into Ubuntu again and this time it said loading Ubuntu Desktop but the login screen that I get is like a terminal which asks me for my username and password. My problem is when that is entered it dumps the following line several times and then reverts back to user@ubuntu$ 

```
Ubuntu login: xxxxx 
Password: 


-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied

user@ubuntu$ 
```

I thought maybe the username or password was incorrect so I tried using a sudo command, this password worked fine. I hope that I made my problem clear, I really need some help. I am not able to get into the GUI login screen only the console one that is not accepting my username and password. I have tried uninstalling ubuntu and reinstalling it as well as trying to use the 9.4 package and have had no luck.  

If anyone has some insight or guidance that they would be willing to share it would greatly appreciated. Thank you in advance. 

Sincerely,
Max

---

### Post by geraldvillorente on 2009-05-08
use the CTRL+ALT+F7(if I'm correct) to shift from CLI to GUI

Check this out [http://www.linuxforums.org/forum/linux-newbie/27030-bash-dev-null-permission-denied-why.html](http://www.linuxforums.org/forum/linux-newbie/27030-bash-dev-null-permission-denied-why.html)

---

