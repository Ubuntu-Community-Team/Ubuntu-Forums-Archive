---
title: "hp-toolbox error not starting"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by shane2peru on 2007-05-19
Ok, I keep trying to run the HP-TOOLBOX so that I can check my ink levels and this is what I get at the command line.  I don't know if I'm running the right command or not.  For some reason it doesn't appear in my menus either.   Here is the scoop from the command line:

```

hp-toolbox 
[COLOR="Red"]error: PyQt not installed. GUI not available. Exiting.
error: PyQt/Qt initialization error. Please check install of PyQt/Qt and try again.[/COLOR]

```

The errors are even actually red on the command line!  I don't know if that means anything, just wanted to point that out :).  Any ideas would greatly be appreciated.

Shane

---

### Post by jasmuz on 2007-05-19
Hey there..

Have you tried installing the missing PyQt ??
Its as easy as "sudo aptitude install python-qt3 python-qt4 -y"

Hit me back with the results!

Take care.

---

### Post by shane2peru on 2007-05-19
> **jasmuz said:**
> Hey there..

Have you tried installing the missing PyQt ??
Its as easy as "sudo aptitude install python-qt3 python-qt4 -y"

Hit me back with the results!

Take care.

Hey that did the trick!!!  Thanks.  I tried installing pyQT to no avail.  :oops:  I guess I needed to know the right packages to install.  

Shane

---

