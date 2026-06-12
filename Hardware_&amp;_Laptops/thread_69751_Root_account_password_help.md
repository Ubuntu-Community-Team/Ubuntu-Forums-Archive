---
title: "Root account password help"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by Mach1 on 2005-09-27
I installed ubuntu but it never asked me to set the root password, i have a project to do open source network in linux. I'm new to linux and need some help i need the root password for the server so if anyone can help me out i would appreciate it.

---

### Post by adwait on 2005-09-27
Uhh........Ubuntu doesn't have a root user.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by XDevHald on 2005-09-27
[quote=adwait]Uhh........Ubuntu doesn't have a root user.
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")[/quote] 
As quoted below, there is a root user but is disabled for only specific needs in doing other work types on your HD.. It is not like the user you have but is a backend user which can do far more than you can with higher permissions in specific areas of the HD.

> Thus the traditional UNIX 'root' account is disabled (i.e. it is not possible to log in as root) 
Please read the entire page as it is recommended to understand the entire use of root and it's capabilities. :)

---

### Post by winblowsconvert on 2005-09-28
You linux people must be all the same, nebulous and evasive, like your trying to protect some pot of gold operating system!  Is it so difficult to tell the guy to just use his own password?   

Besides they could have explained that in the installation process, which is more like a grade schooler wrote it.  I'm a convert from windows too.  Just trying to find a flavor of linux a regular guy can use, not just NASA, a corporate server, or a geek.  It's beginning to look like this system is mean for super freaks with too much time on their hands in order to learn a system that was written decades ago.  

Hard to see this OS or any linux flavor lasting into an even more complex world where time saving automation is the key.  Can't get a straight answer from anyone in the linux community.  Can't listen the music, can't play games (real games), installing anything takes a degree and 5 years of trial and error to maybe, just maybe get anything running.  

Question:  root password?
Answer:  Simple!  Use your own account password!  :smile:

Lengthy unneeded complex instructions at:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by blylett on 2005-09-28
[QUOTE=winblowsconvert]
Question:  root password?
Answer:  Simple!  Use your own account password!  :smile:
[/QUOTE]

For some people yes!, but for others NO. Sometimes your account pw doesnt work as root pw. SO you have to create your own root pw but i dont remember how, i got help with it yesterday but i forgot how, i will reply if i remember :D

---

### Post by XDevHald on 2005-09-28
In order to use permission lines from a user with higher access it is required to use root because of his permission level that is higher than your username.

This does not take a 5 year degree to learn nor is it rocket science, (for some it might be) but using your password is NOT the same as root in which you might be thinking of Red Hat or Fedora in which do use the users password off the top to gain permission as root righ off hand. 

Ubuntu/Debian requires you to set a pasword for root as it is not a setup in the installation.

Hope that clears the sky a bit on this topic.

---

### Post by dbott67 on 2005-09-28
[QUOTE=blylett]For some people yes!, but for others NO. Sometimes your account pw doesnt work as root pw. SO you have to create your own root pw but i dont remember how, i got help with it yesterday but i forgot how, i will reply if i remember :D[/QUOTE]

The instructions are in the thread that adwait posted.  Here are the quick details:

**_Enabling the root account_**

Note: This is not recommended!

To enable the root account (i.e. set a password) use:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root

**_Disabling the root account_**

Note: This is if you have already enabled a root account and wish to disable it again. To disable the root account after you have enabled it use:

sudo passwd -l root

This locks the root account.

---

