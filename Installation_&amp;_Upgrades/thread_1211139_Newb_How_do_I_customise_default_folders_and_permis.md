---
title: "Newb: How do I customise default folders and permissions for any new user?"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by Smartin on 2009-07-12
Hi,

Not sure where this thread should go...

As the admin of a box with lots of other users, how would I go about setting things up so that each new user created on the box is given an environment other than the Ubuntu default.

Say I was starting with a fresh install of Jaunty desktop and I wanted each new user I create have a custom folder/permissions setup.

The standard setup in terms of folders seems to be:

Home/Desktop
    /Documents
    /Music
    /Pictures
    /Public
    /Templates (What the heck is this for...?)
    /Videos

What if I wanted each user to automatically be presented with:
```
Home/Desktop
    /Documents
             /Personal Documents
             /School Documents
    /Music
    /Pictures
            /Private Pictures
            /Shared Pictures
    /Public
           /Dropbox
    /Videos

```
All with non-standard permissions.

Is this even possible?

Simon

---

### Post by sisco311 on 2009-07-12
The /etc/skel directory contains files and directories that are automatically copied over to a new user's home directory when such user is created by the adduser program. I'm not sure, but probably should also work with users-admin(the GUI for managing users and groups).

---

### Post by Smartin on 2009-07-12
> **sisco311 said:**
> The /etc/skel directory contains files and directories that are automatically copied over to a new user's home directory when such user is created by the adduser program. I'm not sure, but probably should also work with users-admin(the GUI for managing users and groups).

sisco311,

I checked that out on someone's (I think yours...?) suggestion but all I can see is two hidden files which seem to be to do with customising bash and then a .profile file.

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

I can't make any sense of that :)

Can you think of anything else?

S

---

### Post by sisco311 on 2009-07-12
You have to create the directory structure in /etc/skel:
```
sudo mkdir -p /etc/skel/Documents/{Personal\ Documents,School\ Documents}
sudo mkdir /etc/skel/Music
...

```

---

### Post by Smartin on 2009-07-12
> **sisco311 said:**
> You have to create the directory structure in /etc/skel:
```
sudo mkdir -p /etc/skel/Documents/{Personal\ Documents,School\ Documents}
sudo mkdir /etc/skel/Music
...

```

sisco311,

Hold on, hold on... this is too easy... ;)

So I just create the folder structure I need within the /etc/skel directory. Yes?

What does the -p flag do?

How about permissions? How do I set them?

Would be great to get this going right... :)

Appreciate your help with this.

S

---

### Post by sisco311 on 2009-07-12
> **Smartin said:**
> sisco311,

Hold on, hold on... this is too easy... ;)

So I just create the folder structure I need within the /etc/skel directory. Yes?
yep.

> **Smartin said:**
> 
What does the -p flag do?


```
sudo mkdir -p /etc/skel/Documents/{Personal\ Documents,School\ Documents}
```
is just a shorthand for:
```
sudo mkdir /etc/skel/Documents
sudo mkdir /etc/skel/Documents/Personal\ Documents
sudo mkdir /etc/skel/Documents/School\ Documents
```

from man mkdir:
```

      -p, --parents
              no error if existing, **make parent directories as needed**
```


> **Smartin said:**
> 
How about permissions? How do I set them?


You can use the chmod command or your file manager.
[uhelp]community/FilePermissions[/uhelp]

If you prefer the gui, then just start your file manager as root:
```
gksu nautilus /etc/skel
```

---

### Post by Smartin on 2009-07-12
> **sisco311 said:**
> You have to create the directory structure in /etc/skel:
```
sudo mkdir -p /etc/skel/Documents/{Personal\ Documents,School\ Documents}
sudo mkdir /etc/skel/Music
...

```

sisco311,

This is very exciting...

I'm finding that I can only *add* folders to the default structure, not completely replace it. Whilst this is a good start it would be great to be able to create a whole new structure.

Possible?

How to I set custom permissions? :)

S

---

### Post by Smartin on 2009-07-12
sisco311,

Sorry to be bombarding you with questions... I'm getting somewhere with this though.

A couple of snags:

1) I'm finding I can only *add* to the existing structure, not replace it completely. How can I replace it completely?

2) (I guess) I can set custom permissions to the folders I create (Haven't tried yet...) but how to I set custom permissions to the existing structure as I can't see it inside the /etc/skel directory?

S

---

