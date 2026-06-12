---
title: "Restore xorg.conf"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by skipsa on 2007-10-01
Hi, while trying to setup an external display, I modified the xorg.conf file in a way that when I get the login screen, it's hardly readable. I manage to login but the screen remains pretty unreadable, which prevents me to navigate to my original file and restore it. Is it possible to access the file through the command line?
Thanks.

---

### Post by Linicks on 2007-10-01
Hit Ctrl+Alt+F1

You should be now in a console.

Log in:

username
password

run:

sudo /etc/init.d/gdm stop


Then run nano text editor:

> sudo nano /etc/X11/xorg.conf

use arrows keys to move around.  Use normal keys to edit (delete, etc.).

Once done, use (within nano) Ctrl+o to save the file (Ctrl+c will cancel and not change anything, Ctrl+x will just exit ditto)

That will save the file and also exit nano editor.

Now start x again:

> sudo /etc/init.d/gdm start

Nick

---

### Post by kestas.j on 2007-10-01
Try to use the following command:

> sudo dpkg-reconfigure -phigh xserver-xorg

It should reconfigure you xorg.

kestas.j

---

