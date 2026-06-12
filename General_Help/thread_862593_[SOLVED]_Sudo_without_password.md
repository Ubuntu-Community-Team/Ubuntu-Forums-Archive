---
title: "[SOLVED] Sudo without password"
date: 2008-07-17
forum: General Help
---

### Post by sebrock on 2008-07-17
I cant for my life get sudo without password to work under Hardy.

I edit sudoers file with visudo. I get no errors or anything when saving.

This is what I have

```

username          ALL = NOPASSWD: commands

```

also tried:
```

username         ALL=(ALL) NOPASSWD: commands

```

Running mythbuntu 8.04.

---

### Post by Vivaldi Gloria on 2008-07-17
Are you putting them below

```
%admin ALL=(ALL) ALL
```

line? It's important that you do. See also my post here:

[http://ubuntuforums.org/showthread.php?t=858700](http://ubuntuforums.org/showthread.php?t=858700)

---

### Post by sebrock on 2008-07-18
Could not get it to work. Done everything by the book (IMO anyways).

I noticed this in the sudoers file:

```

# %sudo ALL=NOPASSWD: ALL

```

with that uncommented it works. Is this some new syntax to Hardy release (or even mythbuntu)? I had no problems with editing sudoers file before.

Thanks anyway

---

### Post by jespdj on 2008-07-18
I guess you want to be able to use sudo without a password for convenience.

I hope you understand that doing that is **extremely unsafe**. If you can run commands as root without any password, then you're essentially throwing any security out of the window.

It is like always leaving the front door of your house unlocked, so that anyone can walk in at any time. Do you really want to do that?!

---

### Post by sebrock on 2008-07-18
The commands are specific and makes no security threat at all. I want it to be able to get my frontend to be as automatic as possible. Its not even exposed to the outside world :) thankx for conserning tho

---

### Post by sebrock on 2008-07-18
Nope, uncommenting and adding myself to group "sudo" still didnt make any difference. Honestly, this is very strange indeed.

My complete sudoers file:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: /usr/sbin/pm-suspend, /sbin/poweroff

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by danwood76 on 2008-07-18
What I would do is create a new group with any old name then add something like this at the bottom:

```

%GROUPNAME ALL=(root) NOPASSWD:/path/to/prgram

```
I think you are editing the wrong line anyway as that line you changed is intended to allow anyone from the sudo group to run anything without a pass.

---

### Post by caljohnsmith on 2008-07-18
Try running the command "groups" to see which groups your username belongs to; make sure you are part of the "admin" group. If you are, then change the line in your sudoers from "%sudo ALL=NOPASSWD: /usr/sbin/pm-suspend, /sbin/poweroff" to using your username (e.g. "john"):
```
john ALL=NOPASSWD: /usr/sbin/pm-suspend, /sbin/poweroff
```
That should work.

---

### Post by danwood76 on 2008-07-18
I just verified this by adding the following to my sudoers file:
```

%synapse ALL=(root) NOPASSWD:/usr/bin/synaptic

```
Adding myself to the synapse group then allows me to run synaptic without typing a password.
I would try recommenting the %sudo line and creating a new group similar to what I just did.

---

### Post by sebrock on 2008-07-18
Yes, finally it worked. First off: to uncomment as the sudoers file suggests does not work at all. Is this a bug or some leftovers from the past?

Creating a new group and adding myself as suggested did however work.

So to sum it up: there is probably a bug here, could anyone confirm this?

---

### Post by danwood76 on 2008-07-18
Theres no bug you are just configuring the sudoers file wrong.

What I posted is correct syntax and it oviously works :)

---

### Post by sebrock on 2008-07-18
Sure it works. BUT the file itself has a line made for this, enable by uncommenting. THAT is what not works.

It is suggested earlier in the thread that it needs to be after the %admin stuff. Well, in that case that line should be changed because it confuses the user.

---

### Post by danwood76 on 2008-07-18
No you dont get the syntax within the file.

That sudo line is supposed to be un commented only, you had added a list of programs to it.
The original line:
```

%sudo ALL=NOPASSWD: ALL

```
When uncommented will allow anyone who is in the sudo group to sudo without giving a password.
This includes inherent risk and leaves you with a system almost as insecure as XP.
To be honest I'm not sure how this differs from lines further down except that I used the alias root within my line which is predefined with all users which probably has something to do with it.
It could have something to do with the fact that the file uses the higher permissions from within the file so it may ignore lines after giving a set of faulty sudo permissions.

When you want to know how to config a file its best to read the man pages which will give you the information you wanted in the first place.
To get man pages you simply type man FILE/APP for example man sudoers gives the manual for the sudoers file.

---

### Post by 1jackjack on 2008-08-26
Just incase any other morons like myself find this thread in their attempt to edit their sudoers, here are some tips that would have saved me some time...

1) add to the bottom of the file as the last entry has the highest priority
2) even if you add NOPASSWD, when you ultimately run these commands, you still have to add the sudo prefix (it just wont ask you for a password obviously)
3) no need to faff around with creating groups; this is what ultimately worked for my needs:
jack ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend, /sbin/shutdown

Hope this helps someone,
Jack

EDIT: another great tip was to avoid using that horrifying editor vi:
add to bottom of ~/.bashrc
export EDITOR=vim
then log out and back in again
then edit sudoers with -E flag:
sudo -E visudo

---

