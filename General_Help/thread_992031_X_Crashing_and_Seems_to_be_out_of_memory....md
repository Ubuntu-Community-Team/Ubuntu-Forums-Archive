---
title: "X Crashing and Seems to be out of memory..."
date: 2008-11-24
forum: General Help
---

### Post by Frantic1337 on 2008-11-24
Hello All,
I am running Hardy Heron and every now and then (like 2 times a day), it seems that X is crashing.  After, none of the windows have title bars and all processes have been killed.  The only way to get this working again is to restart the system.  This seems to happen more when I am doing stuff in FireFox, but it is not only when in FireFox.  I have looked at the system log and it says that I am out of memory, but I have used the system monitor and it looks like I was only using about 1/2 the memory of the system when it crashed today.  I attached a dump of the relavent part of the syslog... Any help that you can give me would be great.  If I wanted to restart several times a day, I would still be on XP...

Thanks,
Matt

---

### Post by ajgreeny on 2008-11-24
Perhaps try running for a while without compiz.  It can cause the symptoms you describe.  Use ```
metacity --replace
``` in the Alt+F2 dialog box to stop compiz.

---

### Post by Frantic1337 on 2008-11-24
Will compiz start back up when I restart the machine?  How can I disable compiz permanently?

---

### Post by ajgreeny on 2008-11-24
On my system when I reboot with compiz switched off, the new session is also compiz free.  You can, however, use a useful application from Forlong which turns it off and on with a single click.  Look at [this site.]("http://forlong.blogage.de/article/pages/Compiz-Switch")

---

### Post by jerrykenny on 2008-11-24
Are you accessing pages with flash content ?  i find flash stuff most promlematic, and use firefoxes "flashblock" to block the content by default.

---

