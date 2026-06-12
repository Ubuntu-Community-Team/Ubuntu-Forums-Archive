---
title: "Root Password Help"
date: 2005-01-20
forum: Installation &amp; Upgrades
---

### Post by fangbite on 2005-01-20
I installed ubuntu linux today and was impressed at several things with it.  Only one problem.  In the instalation process I was never asked for a root password.  Now I need to use the root password, but I have no clue what it is.  Where can I find out what it is so I can change it?  Or did I miss something in the installation process where I needed to give a root password?

---

### Post by crane on 2005-01-20
[QUOTE=fangbite]I installed ubuntu linux today and was impressed at several things with it.  Only one problem.  In the instalation process I was never asked for a root password.  Now I need to use the root password, but I have no clue what it is.  Where can I find out what it is so I can change it?  Or did I miss something in the installation process where I needed to give a root password?[/QUOTE]

There is no root account enabled by default in Ubuntu.
What are you trying to do ?
You should be able to use your user account password when asked.

---

### Post by fangbite on 2005-01-20
I need root access to install something and I have no root password.

---

### Post by tidalwav1 on 2005-01-20
[QUOTE=fangbite]I installed ubuntu linux today and was impressed at several things with it.  Only one problem.  In the instalation process I was never asked for a root password.  Now I need to use the root password, but I have no clue what it is.  Where can I find out what it is so I can change it?  Or did I miss something in the installation process where I needed to give a root password?[/QUOTE]

To set a root password, open a console and run 'sudo passwd'. Then, just type in a password twice, and you should be set. As a side note, to run things as root without actually being root, you can use the sudo command--it will ask you for your own password.

---

### Post by fangbite on 2005-01-20
You mean the password I gave for my default user is the one given to root as well?????  Ok.  Thanks for the assistence.  And I knew about sudo, i just didn't know the password for my account was given to root as well.

---

### Post by poofyhairguy on 2005-01-20
[QUOTE=fangbite]You mean the password I gave for my default user is the one given to root as well?????  Ok.  Thanks for the assistence.  And I knew about sudo, i just didn't know the password for my account was given to root as well.[/QUOTE]

I prefer sudo. Now that I have used it for a while, I know its a good idea!

---

### Post by tidalwav1 on 2005-01-20
The root password is NOT the same as your own password. You use your own password to gain access to the utilitiy to SET the root password. (On a default Ubuntu install, there is no root password initially set; that's why you need to set it with sudo passwd. first sudo will ask you for your own password to get root access, then passwd will change the root password because of sudo.)

---

### Post by pappo on 2005-01-22
[QUOTE=poofyhairguy]I prefer sudo. Now that I have used it for a while, I know its a good idea![/QUOTE]
 I am also having root problems.
I set my root password using "sudo passwd" and it works when I do "su -" in a terminal window.
I can do command line "apt-get install xxxxx" so I know it works.

But when I go to "Computer --> System Configuration --> Users and Groups (for example) , and it asks for my root password there, it doesn't take that same password.
It returns a window which says " Failed to run users-admin as user root:  Child terminated with 1 status"

Any ideas ??

Pappo

---

### Post by Skid on 2005-01-23
If you read up, about sudo you'll see that it uses your user password to gain access to run the application / script as root.  It's a smart application - it's the same for login manager setups, etc..  

So when it asks for a password to setup applications, etc use your user password.

You can learn more about sudo by dropping to a console and typing:

> 
man sudo


Press 'q' to get out of the man pages, once you've finished reading..

---

### Post by arthur on 2005-01-23
[FONT=Georgia]
After 2 years with Linux, I've finally decided to give Ubuntu a try!
I hope to join this community for a long time

 :D 

I have a few problems that I cannot understand  :cry: :

1   During installation, I provided 2 usernames, the first one with administrative privileges, the second one for "normal" use.

Why can't I login with the first user name?

2   When logged in as a "normal" user, and a root terminal launched from the menu, I introduce the administrative user's username and password, but always get an error message

" Failed to run users-admin as user root: Child terminated with 1 status"

HOWEVER (and this makes NO SENSE whatsoever), if I enter my NON-administrative username and pwd, it does open a Root Terminal

Why????

3   In a "normal" user session, a Root Terminal should require authentication (as for step 2 above).

Why is this requirement present ONLY sometimes?

4   I've installed WEBMIN. When trying to open it through my browser, using my administrative user profile, it rejects entry.

Why?[/FONT]

---

### Post by Buffalo Soldier on 2005-01-23
[QUOTE=pappo]I am also having root problems.
I set my root password using "sudo passwd" and it works when I do "su -" in a terminal window.
I can do command line "apt-get install xxxxx" so I know it works.

But when I go to "Computer --> System Configuration --> Users and Groups (for example) , and it asks for my root password there, it doesn't take that same password.
It returns a window which says " Failed to run users-admin as user root:  Child terminated with 1 status"

Any ideas ??

Pappo[/QUOTE]"Computer --> System Configuration --> Users and Groups" is not asking for the root password, but for your current user password... the one that you used for sudo.

Because when you look af the menu entry for "Users and Groups" the command is "gksudo users-admin". Gksudo basically is a GUI that asks for sudo passsword.

---

### Post by Skid on 2005-01-23
[QUOTE=arthur][FONT=Georgia]
2   When logged in as a "normal" user, and a root terminal launched from the menu, I introduce the administrative user's username and password, but always get an error message

" Failed to run users-admin as user root: Child terminated with 1 status"

HOWEVER (and this makes NO SENSE whatsoever), if I enter my NON-administrative username and pwd, it does open a Root Terminal

Why????

[/FONT][/QUOTE]

After two years of running Linux you've not come accross sudo before?

Read my post before yours, and you'll see why.. -> man sudo

---

### Post by cmbroth on 2005-04-22
Quoted
----------------------------------
When logged in as a "normal" user, and a root terminal launched from the menu, I introduce the administrative user's username and password, but always get an error message, " Failed to run users-admin as user root: Child terminated with 1 status" HOWEVER (and this makes NO SENSE whatsoever), if I enter my NON-administrative username and pwd, it does open a Root Terminal
----------------------------------
# Everything about my Hoary Live CD worked perfectly! Wish the installed copy worked so well...

In an effort to administrate my PC, I've tried both passes, both root and my own. I know that root _isn't_ the one it wants, but I tried it anyway. It says *incorrect password*. My (user-level) password is the one that gives me the error message (Child terminated). In the case of synaptic, I've found another way to run it, but that seems a pain. How can we get this to work the way it's supposed to? (Ubuntu 5.04 w/ Gnome, installed today) 

# This is my second distro, my first was also Debian-based. I dual-boot with Windoze until I find a Linux that agrees with me.

---

### Post by matthieufecteau on 2005-05-03
Maybe your problem (with "Child terminated ...etc") is because the loopback interface is not started at boot.  To look further into that direction, read the second post of this thread : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback)

---

