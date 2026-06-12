---
title: "[SOLVED] No Sudo Password for Ubuntu 8.10"
date: 2008-11-19
forum: General Help
---

### Post by Bradleelee on 2008-11-19
In Hardy Heron I edited the visudo file so that when I used the command in terminal

```
sudo shutdown -h 0
```

it would not require me to enter in my sudo password.

Basically I just unedited the visudo line just like it says in the file.  It worked perfectly in Hardy, however when I installed Ibex (8.10) it did not work.  It still requires me to enter in my sudo password. Is this a bug?  If so, is there a work around? I could really use the help on this one.

---

### Post by drs305 on 2008-11-19
I haven't used the Intrepid shutdown command from within the sudoers file but all the other commands I've used work as they did in previous versions.

In the sudoers file, I would enter:
```

# Cmnd alias specification
Cmnd_Alias TEST = /sbin/shutdown

```

As the last line entry:
```

*yourusername* ALL=(ALL) NOPASSWD: TEST

```

---

### Post by Bradleelee on 2008-11-19
Appreciated. I will give it a try.

---

### Post by Bradleelee on 2008-11-19
So I entered it all in and it says that TEST is not a command.

---

### Post by sisco311 on 2008-11-19
works for me.
here is my sudoers file:
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset,insults

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification
[B]Cmnd_Alias TEST = /sbin/shutdown
[/B]
# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
***sisco* ALL=(ALL) NOPASSWD: TEST**


---

### Post by Bradleelee on 2008-11-19
I dont understand why this is not working for 8.10.

This is my first time using an alias for a command, but I entered it in exactly as you have it.  The code I use after I edit the file and press ctrl-o to write out is:

```
sudo TEST -h 0
```

and a lot of combination in between.  I have no problem disabling the sudo password for every command if it is possible in 8.10.  But uncommenting the line:

```
sudo ALL=(ALL) NOPASSWD: ALL
```

does not work anymore.  What am I doing wrong?

---

### Post by drs305 on 2008-11-19
The *command* would still be "sudo shutdown -h 0". By editing the sudoers file what you have done is to allow you to run that command without having to type your password after entering it. 

You haven't created an alias like you are thinking of them; you have created a section in sudoers whose admin commands can be executed without requiring a password.

---

### Post by sisco311 on 2008-11-19
TEST is an alias in the sudoers file not in the shell.

in the terminal you need to type:
```
sudo shutdown -h 0
```


> But uncommenting the line:

Code:
%sudo ALL=(ALL) NOPASSWD: ALL
does not work anymore. What am I doing wrong?

You need to add your user to the *sudo* group.
**NOT** recommended.

---

### Post by Bradleelee on 2008-11-19
Works perfect.  The word 'alias' was a misnomer for me.  Thank you very much for the help!

---

### Post by sisco311 on 2008-11-19
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

