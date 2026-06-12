---
title: "Use of chown / folder with complex names"
date: 2008-10-24
forum: General Help
---

### Post by dagring on 2008-10-24
Hi,

I try to change owner of a file with a complex name (Janine Jansen - Bach - Inventions & Partita). But when I run the chown command, I get the message: Command not found. I suspect this happens because of the name of the file. Is it a way around this without changing the name of the file?

dagr

---

### Post by Archmage on 2008-10-24
Use Tabs to autocomplete the filename.

E.g. J[TAB]J[TAB]B[TAB]

---

### Post by cyfur01 on 2008-10-24
The Tab completion idea should help.

The actual problem is that the shell doesn't interpret spaces as the space character of a filename, but rather interprets it as whitespace seperating variables (ie: multiple file names). You have to "escape" spaces with backslashes (\), or enclose the whole file name with double quotes.

For example:
Janine\ Jansen\ \-\ Bach\ \-\ Inventions\ \&\ Partita
OR
"Janine Jansen - Bach - Inventions & Partita"

Tab completion will insert the backslashes where necessary.

---

### Post by dagring on 2008-10-24
Thanx, it worked. I didn't manage to change permission of the files in the directory. Could you give me a hint?

dagr

---

### Post by geirha on 2008-10-24
Add the -R option to make it recursive. Be careful with what directories you use chown/chmod -R on though, setting the wrong ownership/permissions on vital system files will break your system.

```
sudo chown -R username:groupname "Janine Jansen - Bach - Inventions & Partita"
```

---

