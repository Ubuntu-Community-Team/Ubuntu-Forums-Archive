---
title: "sudo (root) password not working?"
date: 2005-12-01
forum: General Help
---

### Post by Huike on 2005-12-01
I installed ubuntu 5.10 with gnome. Created a user called user1 with password user1password, created root password rootpassword, can login as root or user1 with no problem. But when I login as user1 and do a sudo it asked me for a password, I typed in rootpassword and it said wrong password. If I type user1password it let me execute the command. If I do System/Administration/ Login Screen Setup, the rootpassword was not working but the user1password worked.

I tried to install ubuntu 5.10 on another two PCs and they all did the same thing. Is this a bug or something?

---

### Post by aysiu on 2005-12-01
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by soulestream on 2005-12-01
>  tried to install ubuntu 5.10 on another two PCs and they all did the same thing. Is this a bug or something?

Isnt that the way it is supposed to work?


soule

---

### Post by atoponce on 2005-12-01
When using the sudo command, you are not invoking root, as such, you do not need the root password.  The sudo command pulls users and privileges out of a sudoers file.  So, in your example, when logged in as user1, when typing 'sudo <command>', you will be prompted for the password of the user logged in (user1).  This is not a bug, this is intentional.

Sudo gives you temporary access to the privileges found in the sudoers file.  For Ubuntu, the privileges are similar to root.  On cool thing about the sudoers file, is the logs.  A log can be kept of all the commands executed when a user invokes sudo.  This can help tell what commands are needed, which ones aren't, and which one are being abused.

The help visualize, consider the following scenario.  Suppose you have a company with a number of departments, with employees in each department that use the Linux server.  Say Bob is the printer administrator, and Sally is the web developer.  Bob most likely won't need PHP, Apache, Perl, and other such software utilities at his command.  Rather, he would probably need IP addresses, LDAP, and other utilities.  So, we give Bob the necessary elevated privileges to help him with his job duties, and the necessary elevated privileges to Sally to help her.  We would add these users and the privilges they need to the sudoers file.  When they execute these commands, their password is requested to ensure they want to run that command, incase they may have typed it accidentally.

Hope that helps.

---

### Post by taurus on 2005-12-01
[QUOTE=Huike]I installed ubuntu 5.10 with gnome. Created a user called user1 with password user1password, created root password rootpassword, can login as root or user1 with no problem. But when I login as user1 and do a sudo it asked me for a password, I typed in rootpassword and it said wrong password. If I type user1password it let me execute the command. If I do System/Administration/ Login Screen Setup, the rootpassword was not working but the user1password worked.

I tried to install ubuntu 5.10 on another two PCs and they all did the same thing. Is this a bug or something?[/QUOTE]
Hey, that's the way sudo supposed to work!!!  When you run it, you need to enter your password, not root password...

---

