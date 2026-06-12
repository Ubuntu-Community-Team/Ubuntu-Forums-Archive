---
title: "No root terminal in Jaunty"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by punkybouy on 2009-06-17
I just upgraded to Jaunty from Intrepid on an old Dell Inspiron 2200.  The root terminal is filled in with a reddish color and will not open.  My work around has been to assign a root password, open a regular terminal and su to root if needed.  Anybody got a fix?  Initially opening the root terminal will prompt me for a password but after that it never starts.  Thanks in advance.

---

### Post by LepeKaname on 2009-06-17
> My work around has been to assign a root password, open a regular terminal and su to root if needed. 

You couldn't just use "sudo" ?

I have never used the root terminal, I always run a regular terminal and use sudo for any command I need...

I have Jaunty as well and I can't see where is that root terminal (in the menus)... maybe it is not installed?

---

### Post by Hobgoblin on 2009-06-17
> **punkybouy said:**
> My work around has been to assign a root password, open a regular terminal and su to root if needed.  Anybody got a fix?

No need to set a root password.

sudo *command*

or 

sudo su

---

### Post by dmikulec on 2009-06-18
I, too, would like to use the root terminal again.  I use a command which does not work with sudo. At least the gksu work around does work.

---

### Post by coffeecat on 2009-06-18
> **dmikulec said:**
> I use a command which does not work with sudo.

What command is that? Perhaps you need to read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oldos2er on 2009-06-18
I changed the root terminal command to **gnome-terminal -e "sudo -i"**, which works. Root terminal not working in Jaunty is a known bug.

---

### Post by Amilo1718 on 2009-06-18
> **oldos2er said:**
> Root terminal not working in Jaunty is a known bug.
indeed ;)

---

