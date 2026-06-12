---
title: "How do I assign Password to access Terminal?"
date: 2008-09-15
forum: General Help
---

### Post by W0ZK on 2008-09-15
I have installed the latest release (8.0.4).  On install it ask for a password for log-in use, but I did not see anywhere to give a password for 
use with other functions such as getting the use of terminal.  Is there some way of generating this password after the install?  For me the OS is useless if I cannot access Terminal.

Thanks
w0zk

---

### Post by rbc on 2008-09-15
Applications-->Accessories-->Terminal. You will not need a password to access Terminal, but you will need one to perform certain "superuser" actions ex. sudo fdisk -l. I assume you set yourself up as the first user, so by default, you will be able to do this. By typing sudo in front of the command, you are invoking the superuser rights. You will be prompted for your normal login password. It will not display, for security reasons, but it is being inputted (sorry, that's probably not a real word). Or maybe I completely misunderstood your question

---

### Post by whizbaby on 2008-09-15
Sorry, but what do you mean?
If you don't want to login graphically, use one of the non-graphical terminals, accessible with F1-F7 (gdm is now on F8 I believe) and login with your username and password (the one generated during install).
If you are in a graphical environment, you can open a terminal from the menus (leftmost menu>accessories>terminal), so I dont think thats your problem.

Do you want to execute commands as superuser?
Then do (for example if you want to edit your xorg.conf):
```
sudo nano /etc/X11/xorg.conf
```
simply put 'sudo' in front of the admin-command

Or do you want a root shell?
The root login is disabled by default, but you can still get a root shell doing
```
sudo su -
```
in a terminal. Then you are root. (recommended for rare use only)

was I able to help you somehow?

---

