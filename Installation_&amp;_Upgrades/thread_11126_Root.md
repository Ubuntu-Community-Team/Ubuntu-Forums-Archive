---
title: "Root?"
date: 2005-01-13
forum: Installation &amp; Upgrades
---

### Post by dJCL on 2005-01-13
New here... never installed this distro before, Debian fan all the way lately.
The install was fine, I liked that it picked up on things like my ACPI way better then the current deb installer. Just one problem: root access? It never asked for a root password. I installed, and when it tried to load X it crashed due to a bug in the synaptics driver(alps touchpad really). I could not get access to the config files to modify this.

I just rebooted with the CD, mounted the partition, chrooted and passwd set it. Just more a commenton the install really.

System: Mobile AMD64 2800 in a Eurocom D400K laptop.

Anyway, Enjoy! I know I will.

JC

---

### Post by Boiler98 on 2005-01-14
Ubuntu doesn't use root, it is disabled by default.  You 'sudo' instead -- the first account you set up has full access to the command.

---

### Post by dJCL on 2005-01-14
Guess I missed that somewhere...

Probably when creating the user account it mentioned it...

I'm not one for reading the docs, more of a dive right in type and then fix things that don't act as I expect.

My only issue with having sudo on the user I just created is that doesn't this just put me in the same position as running my desktop as root? could not a smarter malware application test to see if you have sudo permission? I prefer having to enter a password to do root activities then just being allowed to from my desktop.

I may also misunderstand sudo, I obviously have not used it in the past too much.

Anyway...
Enjoy!

JC

---

### Post by wallijonn on 2005-01-14
[QUOTE=dJCL]... doesn't this just put me in the same position as running my desktop as root? [/QUOTE]

No, because you'll still need to give the root password when you enter the Root Terminal. It is the same password as your user password. Unless you explicitly tell it to do something in a root terminal, where your account is given temporary root privs, you will not be able to do anything (root wise) in the user (non-root) GUI.

What malware? Most of that stuff exists in the Windows world.

---

### Post by netsec on 2005-01-14
> What malware? Most of that stuff exhists in the Windows world.
For now.  If a distro allows a user to have root privileges because they logged on normally, then that distro is no better than windows.  Linux could find itself with problems as it strives to replace windows as *the* desktop.

---

### Post by DJ_Max on 2005-01-14
[QUOTE=netsec]For now.  If a distro allows a user to have root privileges because they logged on normally, then that distro is no better than windows.  Linux could find itself with problems as it strives to replace windows as *the* desktop.[/QUOTE]
But thats the thing, a user does not have root privileges unless given to.

---

### Post by Rancoras on 2005-01-15
[QUOTE=netsec]For now.  If a distro allows a user to have root privileges because they logged on normally, then that distro is no better than windows.  Linux could find itself with problems as it strives to replace windows as *the* desktop.[/QUOTE]

The first user account doesn't have root priveleges.  It has sudo priveleges, there's a difference.  Read up on sudo for the details.

---

### Post by dJCL on 2005-01-17
Just trying to straighten this one out...

If I'm logged in as my initially created user, and have a terminal open, then sudo vim /etc/shadow will ask for a password?

But when I'm in that file it shows no password setup for the root user by default. I've messed with my system to set a root password, so I cannot check. But where does sudo decide what password to use when accessing root priveledges?

And using the same password for root as for a user does introduce some(not a whole lot) of security issues. eg some person gets a hold of my user password, then they have root on the system too...

I'm sure once I understand it, It will all make sense...

JC

---

### Post by simple_gifts on 2005-01-17
You can set up the system like other distros by setting the root password

sudo passwd root

---

