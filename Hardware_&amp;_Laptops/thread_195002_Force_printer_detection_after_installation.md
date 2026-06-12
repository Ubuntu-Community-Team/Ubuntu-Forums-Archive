---
title: "Force printer detection after installation"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by GozzoMan on 2006-06-12
Hi all,
   hope not to waste your time asking a question answered a thousand times, but I don't seem to find answer in the forums or documentation to this seemingly simple issue.

Simply put: if I connect and turn on my printer (canon bjc-240) during installation, it's recognized and installed just fine, but if I don't during installation, I'm not able to have it detected afterwards (nor to have it properly function manually choosing the model), not even by rebooting.

So: how can I execute after installation the same printer detection mechanism which is run during installation?

Thank you.

---

### Post by GozzoMan on 2006-06-13
Ehm, I installed printconf hoping to solve with it. I've gone for:

[INDENT]sudo printconf[/INDENT]

and what I got is:

[INDENT]*** glibc detected *** double free or corruption (!prev): 0x0816e838 ***
Unable to read printer database.  Please ensure the "foomatic-db" package is
installed properly.[/INDENT]

foomatic-db is reported by synaptic as installed, I think as a part of the default installation (please note it's a very fresh Dapper installation from scratch).

Well, d'oh. :|

---

### Post by Giorgis on 2006-06-14
[QUOTE=GozzoMan]Ehm, I installed printconf hoping to solve with it. I've gone for:

[INDENT]sudo printconf[/INDENT]

and what I got is:

[INDENT]*** glibc detected *** double free or corruption (!prev): 0x0816e838 ***
Unable to read printer database.  Please ensure the "foomatic-db" package is
installed properly.[/INDENT]

foomatic-db is reported by synaptic as installed, I think as a part of the default installation (please note it's a very fresh Dapper installation from scratch).

Well, d'oh. :|[/QUOTE]
I have the exact same problem and this is June 2006. Can somebody help with this one 

G

---

### Post by accoreturn on 2006-08-15
I, too, had this problem.  I noiced on another post([http://www.ubuntuforums.org/showthread.php?t=101317]("http://www.ubuntuforums.org/showthread.php?t=101317")) where a user by the name of Alarson mentioned, > I installed gnome-cups-manager and it installed my HP882C printer without incident.

My fresh install of Ubuntu Dapper had gnome-cups-manager, of course, so no need to install.  I ran it and everything worked out just fine for my HP-PSC-1210.

-Hank

---

