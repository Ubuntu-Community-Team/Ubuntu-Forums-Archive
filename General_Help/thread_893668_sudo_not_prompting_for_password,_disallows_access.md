---
title: "sudo not prompting for password, disallows access"
date: 2008-08-18
forum: General Help
---

### Post by riverfr0zen on 2008-08-18
Sudo has suddenly started to behave this way:

shell:~$ sudo ls -l /home/
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts

On calling the command, it simply automatically repeats 'Sorry, try again' (without prompting the user for a password), then finally fails as above.

The only thing I can think of that may be causing this is that I changed the root user's password while su -'d as the root user.

Any ideas about fixing this?

---

### Post by fsmithred on 2008-08-18
sudo uses the user's password.

---

### Post by riverfr0zen on 2008-08-19
Yes, I know. However, the problem is that sudo is not allowing users to enter a password. There is no password prompt. It simply automatically returns 'Sorry, try again.' three times, then quits.

And no, none of my keyboard keys are 'stuck' ;)

---

### Post by mb_webguy on 2008-08-19
Are the users in the admin group?

---

### Post by p_quarles on 2008-08-19
> **mb_webguy said:**
> Are the users in the admin group?
Make sure they are, of course, and it would also be helpful if you posted the contents of /etc/sudoers.

---

### Post by michael_1234 on 2008-08-19
If the user is not in the sudoer's file, you'd still be prompted for a password.

The correct, expected usage  -- if giving *wrong* password:
$ sudo ls -l /home/foo
[sudo] password for userxyz: 
Sorry, try again.
[sudo] password for userxyz: 
Sorry, try again.
[sudo] password for userxyz: 
Sorry, try again.
sudo: 3 incorrect password attempts


If the user is NOT in the sudoer's file, you'd still be prompted,

$ sudo ls -l /home/foo
[sudo] password for userxyz: 
userxyz is not in the sudoers file.  This incident will be reported.


Here's just a wild idea... what exactly is your "ls" doing, and "sudo"? Do you have aliases?  Also, which shell is being used?

~$ type ls
ls is aliased to `ls --color=auto'

$ type sudo
sudo is hashed (/usr/bin/sudo)

~$ echo $SHELL
/bin/bash


Try using bash (which you should be using, anyway),
$ bash -i
$ sudo ls -l /home/foo
....?


Good luck,
-m

---

### Post by riverfr0zen on 2008-08-19
I figured out the issue. The problem wasn't quite with sudo, but that my /dev/tty had somehow turned into a text file - the output from sudo was being written to this /dev/tty text file.

I restored /dev/tty to a character device (as it should be) and the issue disappeared.

---

