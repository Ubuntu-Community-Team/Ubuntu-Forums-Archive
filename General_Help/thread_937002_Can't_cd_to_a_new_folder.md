---
title: "Can't cd to a new folder"
date: 2008-10-03
forum: General Help
---

### Post by RJWEcology on 2008-10-03
Hey, I'm a new user to Ubuntu (I came from openSUSE) and I'm having trouble changing from my home folder to a sub-folder inside. I've set a su password and have logged in as su but when I try to cd to the new dir, it won't let me!? It worked fine before in suse but it won't let me here!? 

e.g. 

```
rich@Obsidian:~$ su
Password: 
root@Obsidian:/home/rich# ls
Desktop    Examples    Music     Public     Videos
Documents  Light Zone  Pictures  Templates
```

when I do this...

```
root@Obsidian:/home/rich# cd Light Zone
bash: cd: Light: No such file or directory
```

I notice the Folder Light Zone is highlighted green and is in blue writing. What does that mean? (I know different colours mean different things). 

I'm sure it's something painfully simple, so please feel free to show me up :D - By the way, I'm loving Ubuntu! It works 100x faster and better on my system. I'm gonna be staying with this distro for a while! Great work guys! 

Rich

---

### Post by vishzilla on 2008-10-03
use tabs for folders with spaces. After typing Light press tab or you can use escape character \ for a space like ```
cd Light\ Zone/
```

---

### Post by Ryadt on 2008-10-03
cd 'Light Zone' 
should do it.

---

### Post by doug1212 on 2008-10-03
Hi,
Wrap the path in quotes if it contains a space

```
cd 'Light Zone'
```

Doug

---

### Post by RJWEcology on 2008-10-03
Ahh, the quotes worked. Thanks for the help.

---

