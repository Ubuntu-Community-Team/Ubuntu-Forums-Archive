---
title: "noobish question: won't I fill up my HD?"
date: 2008-07-28
forum: General Help
---

### Post by joey129 on 2008-07-28
I don't know exactly how updates work, but there always seems to be something to update in Ubuntu. Now, I don't know exactly how updates work but won't I eventually fill up my hard drive if I regularly update?

---

### Post by Potatoj316 on 2008-07-28
No, it shouldnt be a problem.  The updates are small and usually replace the older files.

---

### Post by sayakb on 2008-07-28
Updates are stored in /var/cache/apt/archives
To remove them, do:
```
sudo apt-get clean
```
Note: The above command will **not** uninstall the programs but just remove the installers..

---

### Post by argail1980 on 2008-07-28
btw: apt-get upgrade tells you how much more (or less) disk space will be used after upgrade.

---

