---
title: "how can you make a program ignore files?"
date: 2008-09-03
forum: General Help
---

### Post by malachi1990 on 2008-09-03
So I straced rhythmbox, and found that it was accessing two files that apparently don't exist.  How can I get around this?

Any help is appreciated.

---

### Post by Gannon8 on 2008-09-03
What two files? Try reinstalling the program.

---

### Post by malachi1990 on 2008-09-04
Thanks for the idea (silly me!) about reinstallation, didn't work though.

The specific files were /usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION and  /usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/messages.mo

---

### Post by porchrat on 2008-09-04
looks like you have an encoding problem.

try this command to reset your locales:

```
sudo dpkg-reconfigure locales
```

hopefully it will help

---

### Post by malachi1990 on 2008-09-04
Thanks, but that didn't work. It appears that the gui of the program is not coming up until every other time, instead of the program itself not responding.

---

