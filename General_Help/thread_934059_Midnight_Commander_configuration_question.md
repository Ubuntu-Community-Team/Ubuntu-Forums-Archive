---
title: "Midnight Commander configuration question"
date: 2008-09-30
forum: General Help
---

### Post by milan_ns on 2008-09-30
I have some small MC configuration issues that are really annoying :D

- Each time I start MC, the right pannel shows the root directory, instead of remmembering the last directory used (as it does on RHEL4) - left panel is fine, it remmembers the last used dir.
- When I exit MC with F10, I'm back at the directory from which I started the MC, instead of the directory set in the selected panel.

Does anyone knows how to fix this :confused:?

Thanks!!

---

### Post by supernintendo on 2009-03-07
If you use bash, you can add 
```
alias mc='. /usr/share/mc/bin/mc-wrapper.sh'
``` in .bashrc at your home directory. For other shells try 'man mc'.

---

