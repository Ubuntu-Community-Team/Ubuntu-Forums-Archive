---
title: "Highlight on Files"
date: 2008-07-16
forum: General Help
---

### Post by allinurl on 2008-07-16
Hello, I was wondering why Am I getting highlights on certain files, I know is because of the permissions, but in my other machine same files are not displayed highlighted. Is there a way to get rid of this? Thanks

---

### Post by dracayr on 2008-07-16
enter 

alias ls=ls

at the command line

dracayr

---

### Post by allinurl on 2008-07-16
but is there a way to keep the rest of the colors except using a background highlighting? What I mean is I wanna keep colors, but not the ones with background highlight. Thanks

---

### Post by dracayr on 2008-07-16
No. ls has three options of coloring: --color=auto --color=never and --color=always. Probably your other computer simply has an older version of ls (check with ls --version). But, to be honest, the coloring is nothing bad is it??? to re-enable coloring, execute ```
alias "ls=ls --color=auto"
```

dracayr

---

