---
title: "Changing user privileges entirely from BASH shell"
date: 2008-11-17
forum: General Help
---

### Post by Tony Youngblood on 2008-11-17
Greetings all,

Ubuntu Intrepid Ibex 8.10

I'm seeking a way to create a user and alter her privileges entirely from a bash terminal.  When I say privileges, I am referring to System/Administration/Users and Groups/Properties/User Privileges.   (Options such as "Access external storage devices automatically" and "Monitor system logs".)  I want to do this entirely in bash because I am experimenting with setting up new users remotely through ssh.  (We also tried going GUI with tightvnc and a graphical interface, but the user privileges were disabled, I suspect because we were on screen environment 1).

At any rate, there would almost HAVE to be a way to set this up through a bash terminal.  Obviously, the first step is:

$ adduser username admin
(to add user and give admin privilege).  

But I am at a loss to figure out how to add the other privileges.  A fairly-thorough internet search and a man-hunt on all the relevant commands (adduser, usermod, etc) have yielded nothing.  

Again, I understand how to go about this with the Ubuntu graphical interface.  I'm trying to do this with bash.  Any ideas?

Best,
Tony

---

### Post by kerry_s on 2008-11-17
what i do is just manually add the user to the groups i want them in.
sudo vi /etc/group

it's simple you just add the user name to the group you want them in, i just had to do mine, cause i did a debian expert install i selected to use sudo with no root login and it screwed it up, the only user was root and it didn't even install sudo. :confused:
so i used the adduser, then edited the group file to give access to the right things.

---

### Post by geirha on 2008-11-17
A couple of commands that may help
```

groups *username*        # shows all the groups *username* is member of
getent group *groupname* # shows all members of group *groupname*

```

---

### Post by ezsit on 2008-11-17
adduser 

-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
    A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with the -g option. The default is for the user to belong only to the initial group.

There are a lot more features listed in the man page for adduser.

the usermod command also has some features you might want after a user has been created. The man page is also helpful for more detail.

---

### Post by Tony Youngblood on 2008-11-18
* slaps self on head

Apparently, my confusion stemmed from the fact that I didn't realize a privilege and a group are the same thing.  No wonder the man pages made no mention of privileges!  At any rate, armed with this one piece of basic-yet-valuable information and the helpful forum posters, I was able to solve the problem.  Here's what I learned:

First, I used Geirha's suggestion of
$ groups username
on an already set-up user to find out the names of the privileges I wanted to add.

If I wanted to add only ONE privilege, I could do so by:
$ sudo adduser username groupname

However, it won't allow me to add multiple groups.  To do it this way, I'd have to repeat the command multiple times.

The suggestion of ezsit to do this:

adduser
-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]

is actually an option of useradd and not adduser.  But when I try the command: $ sudo useradd --groups group1,group2,group3 username
here's what I get:
useradd: user username exists

Of course, if I have yet to create the user, this method would work beautifully.  But I have.  So, instead:

$ sudo usermod --groups group1,group2,group3 username

. . .and my user is given my specified privileges.  The thing to be aware of, however, is that this command REPLACES the groups rather than appends them.  So if I usermod groups cdrom and audio, then my user will ONLY have those two groups.  So, I have to include every group I want regardless if the user is already a member.

It would be nice to find a method that would append groups rather than replace them, but for my purpose, this method is adequate.

---

### Post by geirha on 2008-11-18
Try something like this script. It should add a user to all groups another user is added to, except that user's primary group (gid). (Can't test the script myself right now, so I might have done a syntax error here and there)

```

#!/bin/bash

if [ $# -ne 2 ] || ! getent passwd $1 $2 >/dev/null; then
  echo "Usage: $0 reference_user user_to_modify"
  exit 1
fi

primary_group=$(id -gn $1)

for group in $(groups $1); do
  [ $primary_group = $group ] && continue  # skip the primary group
  sudo adduser $2 $group
done

```

---

