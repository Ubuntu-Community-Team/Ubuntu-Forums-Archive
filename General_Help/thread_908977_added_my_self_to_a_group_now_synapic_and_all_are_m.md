---
title: "added my self to a group now synapic and all are missing"
date: 2008-09-03
forum: General Help
---

### Post by rob1101 on 2008-09-03
I recently added my self to a group with 

```
sudo usrmod -G virtualboxusers
```
or something along those lines.

I then logged in to find that all the shortcuts to synapic, loginwindow(i think thats what its called), add remove programs are missing. However ```
gksudo synaptic
``` still works fine. This also took away my ability to use sudo so I edited the ```
/etc/sudoers
``` file and now I can use sudo, but still I am missing alot of shortcuts in System>administration.

---

### Post by iaculallad on 2008-09-03
What displays when you issue the command below on your terminal:

```
groups
```

---

### Post by rob1101 on 2008-09-03
```
robert
vboxusers
```

---

### Post by iaculallad on 2008-09-03
Try to add your username to the admin group:

```
sudo useradd -G admin your_username
```

Then do a log-off then log back in.

EDIT: Actually, you did not add yourself to virtualboxusers. What you did is modified your user account. To add to a group, you should have done useradd.

---

### Post by rob1101 on 2008-09-03
Ahh ok useradd would be the command that I should have used. 

I tried
```
sudo useradd -G admin robert
``` 
and it said "user robert exists"

So how would I undo what I did and do it the correct way?

---

### Post by DrMeers on 2008-09-04
useradd is used to "create a new user or update default new user information"

I think your inital usermod command was correct, you just missed the '-a' (append) option -- without this, it removes all of your initial groups!

```

$man usermod
...
       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option. If the user is
           currently a member of a group which is not listed, the user will be
           removed from the group. This behaviour can be changed via the -a
           option, which appends the user to the current supplementary group
           list.
...

```

 -- ie. should have been:

```
sudo usrmod -a -G virtualboxusers
```

Not sure how to find out which groups you've been removed from though...

For reference, my groups are:
```
simon adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
```

---

### Post by Oldsoldier2003 on 2008-09-04
Aas DrMeers pointed out sudo usermod -aG vboxusers was the appropriate command to run. Since you have removed yourself from the admin group your best bet is to reboot choosing recovery mode from the grub menu. Then use usermod to readd your user to the appropriate groups. (Don't forget the -a) once you have done this, reboot into the gui and everything should be OK.

 If not, make another user and give it administrative rights using the gui tool Users and Groups. Then run sudo id username to get all the groups from your freshly minted admin account. you can then run usermod again and add any groups you might have missed to your old account. Once complete you can always delete the new account, or leave it active for some emergency down the road.

---

### Post by rob1101 on 2008-09-04
thanks guys for clearing that up. However i fixed the problem another way in the recovery mode. 

I added my self to the sudoers file 

/etc/sudoers
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
**robert    ALL=(ALL) ALL**

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Is what I did alright? Secure? 

after I got that done I could use sudo among other things. then I used uesermod -aG

---

### Post by Oldsoldier2003 on 2008-09-04
As long as you removed yourself from sudoers after you fixed everything you don't have any security issues. I would not recommend leaving your account set to all and no password.

---

### Post by rob1101 on 2008-09-04
alright I removed it and everything still works fine with a restart as far as I can tell. 

Isn't that no pass word bit commented out?

---

### Post by Oldsoldier2003 on 2008-09-04
yes it is. Its late here and I didnt notice :) The cool thing is that you thought outside of the box and came up with another workable solution.

That is a very valuable skill when working with Linux- there are many ways to skin a cat and all that matters is the end result.

---

### Post by rob1101 on 2008-09-04
hehe, not really thinking outside the box :P just using what I know. But your right if it works thats all that matters :)

Thank you for all the help

I love ubuntu forums

---

### Post by myidbe on 2008-09-11
This was a very helpful post. I had the very same problem while following a "linux for beginners" tutorial. Actually the tutorial is an official code.google.com tutorial ([here]("http://code.google.com/edu/tools101/linux/ownership_permissions.html"))...suprising...

Anyway, I was able to boot the computer in recovery mode, and add myself to the admin group again without any problems and without ever having to enter a password - which I found a bit odd. In fact that seems really insecure. I was under the impression that my user password was also the root password (it was always the password I used for sudo at least). Do I need to add/change the root password to prevent someone from being able to change everything about my system by just restarting in recovery mode?

---

### Post by rob1101 on 2008-09-11
yes from the terminal,

```

sudo passwd root

```

this will change the root password. And make your system more secure.

---

