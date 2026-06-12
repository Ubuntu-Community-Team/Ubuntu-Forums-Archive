---
title: "[SOLVED] what's happened to su or sudo -"
date: 2008-07-27
forum: General Help
---

### Post by superjacent on 2008-07-27
I've just installed 8.04.    I'm trying to edit the grub loader file so that Windows is the default operting system.  From terminal, I'm sure I use to do this:

```
steve@steve-desktop:~$ su
Password: 
su: Authentication failure
steve@steve-desktop:~$ 
```

But as you can see, an Authenticiation Error.   I've definitely entered the correct password.

Is there a new way of doing things.   Any help appreciated.

---

### Post by tamoneya on 2008-07-27
the command "su" give you root privileges and effectively logs you in as root.  You do not have this password since it is intentionally not set during the install since logging in as root is strongly discouraged in ubuntu.  Instead you should use sudo.  The password that sudo prompts for is your password.
Basically instead of running this:```
su
apt-get update
apt-get upgrade
```
you should run this:```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by superjacent on 2008-07-27
Thanks for your reply.   In order to edit the menu.lst file, what command or series of commands do I use.

When issuing a sudo command, this is what I get;

```
steve@steve-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
steve@steve-desktop:~$ 
```

Any help appreciated.

---

### Post by bjschuma on 2008-07-27
> **superjacent said:**
> 
When issuing a sudo command, this is what I get;

```
steve@steve-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
steve@steve-desktop:~$ 
```Any help appreciated.

When using sudo, you also have to give the command that you wish to run.  For example, to open gedit with root privileges you would run "sudo gedit"

---

### Post by superjacent on 2008-07-27
Thank you.  It worked.

---

### Post by PmDematagoda on 2008-07-27
If you want to attain full root privileges through sudo such that it is equivalent to su or su -, then you need to run:-
```
sudo -i
```

---

### Post by tamoneya on 2008-07-27
basically if you have the command ```
nano /boot/grub/menu.lst
``` and you need root permissions you can preceed the command like this to gain root permissions for just the following command and nothing else.  ```
sudo nano /boot/grub/menu.lst
```By doing it like this you cant by accident leave root sessions open resulting in a more secure system.

EDIT: sorry about the late post.  My internet is REALLY sluggish tonight and it took me 20 min or so before I got a strong enough connection to transmit.

---

### Post by superjacent on 2008-07-27
No problems, really appreciate your help.

---

