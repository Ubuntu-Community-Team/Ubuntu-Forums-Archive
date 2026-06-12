---
title: "Root (Superuser)"
date: 2008-09-28
forum: General Help
---

### Post by mellis7 on 2008-09-28
I have just installed ubuntu 8.04 on my roomates computer and i need the root password. what is it by deafault password.

I know i cant login using the login screen im using the su command and it wont let me into anything without a password.

---

### Post by Naiki Muliaina on 2008-09-28
Its your main users password, if you only have 1 user name, its the password you use for that :)

---

### Post by The Cog on 2008-09-28
In Ubuntu, the root account is disabled. You can use **sudo** in front of any command you want to run as root, or **sudo -i ** to elevate your console to root priviledge for more than one command.

See this link:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by greja on 2008-09-28
I am new in linux.I have just installed 8.04 desktop edition in my laptop. At the time of installation I craeted a  user and I can login using that. But each time I have to use sudo for most command.So, I tried to login as root, but failed. Whate is root password? I did not get any option to set root pasword at the time of installation.

---

### Post by Naiki Muliaina on 2008-09-28
As Cog says, Root is disabled in Ubuntu. Your root access password for using Sudo is your first accounts password.

---

### Post by jerome1232 on 2008-09-28
Look at posts 2 and 3 to sum them up:

There is no root password by default in Ubuntu, login to root account is disabled.

Ubuntu uses sudo to elevate privileges to root, or any other user. You just prepend your command with the 'sudo' command and it will prompt you for a password, you need to use whatever users password you are logged into.

sudo -i will get you into a root prompt, it also asks for the users password.

---

### Post by greja on 2008-09-28
Thanks cog for your link. I got some knowledge from there. But one thought in my mind.... who is more brilliant? Dennis Ritchie or Ubuntu creators:confused:

---

