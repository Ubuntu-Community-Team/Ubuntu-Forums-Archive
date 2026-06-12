---
title: "Gutsy, system shows Floppy1 but no floppy drive"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by Walter Jr on 2007-10-25
Installed Gutsy on my Gateway last night and finished up today. Everything seems fine. Got ccsm up and running and also wine. I notice that my floppy light on the laptop stays on an awful lot. Funny thing is I don't have a floppy drive on the laptop.
In Places/Computer if I do a properties on the Floppy1 it shows:

Type: folder
Contents: nothing
Location: computer:///
Volume: Root Volume
Free space 22.3 GB

When I do a properties on the Filesystem it shows an nice piechart with 22.3 GB free space also with a location of computer:///

Is this normal for the floppy1 to show up when there is no floppy. If I try to open it all I get is a box that says 'Opening "Floppy 1" You can stop this operation by clicking cancel' but nothing ever happens.

Should I ignore or try to fix?

Thanks

---

### Post by odysseusjak on 2007-10-25
I have a similar problem.  I don't have a floppy drive either but Nautilus shows one.

---

### Post by odysseusjak on 2007-10-25
I found the answer, Walter Jr.  Open up a terminal and type sudo gedit /etc/fstab.  Enter your password.  Comment out (i.e., put a number sign -- # -- next to) the floppy drive line.  Save it and exit.  You should be good to go.

---

### Post by Walter Jr on 2007-10-25
Thanks odysseusjak, commented out the line that had /dev/fd0 and it worked like a champ.

---

### Post by odysseusjak on 2007-10-31
You're welcome, Walter Jr.

---

### Post by Dave_Connor on 2008-03-23
Found this topic and it fixed this bug. Thank you. :)

---

