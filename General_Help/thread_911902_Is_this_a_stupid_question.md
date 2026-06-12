---
title: "Is this a stupid question??"
date: 2008-09-06
forum: General Help
---

### Post by nuke_fluke on 2008-09-06
Why am I not a system privileged user on my own system?

How can I be a root user ... or  can I?
by default terminal shows $ symbol ...

---

### Post by iaculallad on 2008-09-06
> **nuke_fluke said:**
> Why am I not a system privileged user on my own system?

It's for security purpose. That you're still given a chance to issue your privilege password in order for you to change delicate settings which can break your system's stability (Giving you the chance to think first before you proceed).

> **nuke_fluke said:**
> How can I be a root user ... or  can I?
by default terminal shows $ symbol ...

You can be a root user by executing the terminal commands below:

```
sudo -i
sudo su

```

Issuing the commands below and with successful credential entry, terminal would give you the # sign and not $. 

-You have to issue your own password here.

And remember that by default, The root account is disabled by default.

---

### Post by nuke_fluke on 2008-09-06
So any user can be a root user and damage the system??
(like guest login account user)
by issuing the commands you have written from the terminal....

Or is it the one who is the system admin...?

---

### Post by pbotros1234 on 2008-09-06
To become root and get a #, you type either "sudo su" or "sudo -i", and then it will prompt you for the root password. Enter in the right password, and you will granted root access and a #.

Any account can do "sudo su", even guests, but you need to know the root password.

---

### Post by Bliepo32 on 2008-09-06
> **nuke_fluke said:**
> Why am I not a system privileged user on my own system?

So that if you happen to open a virus, it won't kill your harddrive. That's why.

---

### Post by sisco311 on 2008-09-06
> **nuke_fluke said:**
> So any user can be a root user and damage the system??
(like guest login account user)
by issuing the commands you have written from the terminal....

Or is it the one who is the system admin...?

Only the users who are in the *admin *group can use [I]sudo.
[/I]You can use the *groups <username>* command to list the groups,
and *sudo usermod -a -G admin <username>* to add a user to the admin group.

---

### Post by steveneddy on 2008-09-06
**[COLOR="Blue"]Is this a stupid question??[/COLOR]**

No

---

### Post by lukjad on 2008-09-06
There are no such things as stupid questions. Only stupid people who say that questions are stupid.

---

### Post by hyper_ch on 2008-09-06
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

