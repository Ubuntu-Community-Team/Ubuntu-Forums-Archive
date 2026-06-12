---
title: "[SOLVED] SUID SGID and Stikcy: what this 3 means when i chmod in remote files in gftp"
date: 2008-11-13
forum: General Help
---

### Post by Awareness on 2008-11-13
when i chmod in gftp in some remote files, it gives me several "special" options: SUID SGID and sticky... do you know what this 3 means?

---

### Post by bab1 on 2008-11-13
The sticky bit is changed from it's original use.  Currently it's used to suppress deletion of the files that belong to other users in the folder where you have "write" access to.

The others are for setting the UID or GID upon an executable file when used.  For directories it also may mean that when a new file is created in the directory it will inherit the group of the directory (and not of the user who created the file).

See [[COLOR="Red"]**here**[/COLOR]]("http://lokams.blogspot.com/2008/03/about-suid-sgid-and-sticky-bit.html")

Edit:  Link repaired.

---

### Post by Awareness on 2008-11-13
Thanks, i looked for it but I couldn't find anything meaningful... maybe because I was thinking just in ftp terms :)

Btw, the link is broken, you add an extra http// at the begining ;)

---

