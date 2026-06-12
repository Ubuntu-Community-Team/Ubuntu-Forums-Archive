---
title: "Help!!!  Ubuntu is not recognizing admin acct"
date: 2008-11-23
forum: Hardware
---

### Post by caroline121 on 2008-11-23
Hi, all!  I am pretty new to Linux and Ubuntu, but desperately need some help.  

Ubuntu isn't recognizing the admin acct I set up on my laptop, and only recognizes the user (who doesn't have admin privileges).  I'm thinking I need to reinstall from scratch, but Ubuntu doesn't recognize the CD drive through the system BIOS.  

Any help would be much appreciated!!!

Carrie (PM messages are allowed!!!):KS

---

### Post by cdtech on 2008-11-23
I'm thinking if you don't know your root password you may need to reinstall......

You can't log in as "root", you need to use the "sudo" command to do any administration task.......

---

### Post by caroline121 on 2008-11-23
It's not recognizing the root password.  How do I use the "sudo" command?  I need step by step instructions as I am brand new to Linux.

Thanks for your help!!!

---

### Post by Mewshi on 2008-11-23
You use 'sudo' followed by the command you want to run.  Like, if I want to delete a file as root, I will put in "sudo rm file.example" minus the quotes.

It will then ask for your password; also, sudo stays in effect for a certain length of time.

Best of luck to you! ^-^

---

### Post by aysiu on 2008-11-23
There is no root password.

There is only your user password.

Some users (for example, the one created during installation) have the ability to use their passwords to temporarily assume root privilege for certain tasks. Other users can not.

If you want to make sure your user account is able to sudo, follow these instructions:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by aysiu on 2008-11-23
There is no root password.

There is only your user password.

Some users (for example, the one created during installation) have the ability to use their passwords to temporarily assume root privilege for certain tasks. Other users can not.

If you want to make sure your user account is able to sudo, follow these instructions:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

