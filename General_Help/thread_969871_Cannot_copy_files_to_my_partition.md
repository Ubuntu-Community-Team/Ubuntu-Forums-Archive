---
title: "Cannot copy files to my partition ?"
date: 2008-11-03
forum: General Help
---

### Post by NathanDC on 2008-11-03
I cannot copy (write) any files to my partitions. It says I have to be logged in as "root". Anyway around this?

My other question is that since I'm not familiar with Ubuntu's user/group permissions I ended up deleting all the groups except root and now my user account is pretty limited. anyway i can repair this or if I can stay logged in as root?

I use my laptop as a tech and I am constantly needing to perform tasks fast. 

thanks for any help.

---

### Post by beno1990 on 2008-11-03
If you're copying the files from the terminal, put "sudo" before any command. Or if you're doing it from Nautilus, open a terminal and type

```
sudo nautilus
```

This will give you full access to all files on the computer, so be careful.

---

### Post by NathanDC on 2008-11-03
Thanks! I really love the OS. I just want to get everything ironed out

---

### Post by NathanDC on 2008-11-03
I have one more question. I was RDP'd in to a XP machine with my disk shared and I could not copy anything from the machine I was RDP'd into to my drive? Same problem of not being logged in as root. 

Because I notice it does not prompt you to perform "root" tasks i guess unless you are going through the terminal?

---

### Post by beno1990 on 2008-11-03
Most programs which need root access will prompt you to enter the sudo password in one form or another. Most programs on the System -> Administration list will prompt you for a root password when you open them, for example.

There's no right or wrong way to open a program as root, but for a program like Nautilus (which you don't need to have root access for most tasks) you're probably better using sudo in the terminal or pressing alt+F2 and entering sudo nautilus there.

---

### Post by oldos2er on 2008-11-03
> **beno1990 said:**
> 
There's no right or wrong way to open a program as root, but for a program like Nautilus (which you don't need to have root access for most tasks) you're probably better using sudo in the terminal or pressing alt+F2 and entering sudo nautilus there.

 Except with a graphical program like Nautilus, you want to use gksu in place of sudo.

---

### Post by scouser73 on 2008-11-04
> **NathanDC said:**
> I cannot copy (write) any files to my partitions. It says I have to be logged in as "root". Anyway around this?

My other question is that since I'm not familiar with Ubuntu's user/group permissions I ended up deleting all the groups except root and now my user account is pretty limited. anyway i can repair this or if I can stay logged in as root?

I use my laptop as a tech and I am constantly needing to perform tasks fast. 

thanks for any help.

When you log in as Root using the command **gksudo nautilus** you can change the permissions of your drives so that you have control; paste, cut, copy, rename etc. Click on the Permissions tab to perform the changes.

---

### Post by NathanDC on 2008-11-05
thank you. That has solved my problems.

---

