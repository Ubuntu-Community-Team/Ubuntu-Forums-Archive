---
title: "Editing files in JOE creates another file"
date: 2008-10-22
forum: General Help
---

### Post by eludlow on 2008-10-22
Whenever I edit a file in JOE (in fact, just tried - same in EMACS) and save it, I get another files created xx.yyy~ - what's that all about?  Is there a way I can stop it the file with the wiggle after it being produced?

Thanks,
Ed Ludlow

---

### Post by geirha on 2008-10-22
It's a backup of the file before you edited it. It can be turned off by using -nobackups on the command-line, or putting a line with ```
nobackups
``` in ~/.joerc

```
man joe
```

---

### Post by eludlow on 2008-10-22
Thank you!

---

### Post by jblackhall on 2008-10-22
Is there a way to make these ~ backups get deleted automatically, like say on reboot?

---

