---
title: "[SOLVED] Directory is there but I can't open it"
date: 2008-07-13
forum: General Help
---

### Post by upchucky on 2008-07-13
When i do this, I can see the directory, but when i try to cd into it it fails.

I can open the directory using gnome commander, but I need to be able to be able to work it in the terminal to modify how it starts in wine, as I can't set up log files unless i can access it in the terminal.


```
electric@XPS-Laptop:~$ cd /home/electric/.wine/drive_c/
electric@XPS-Laptop:~/.wine/drive_c$ ls
Program Files  windows
electric@XPS-Laptop:~/.wine/drive_c$ cd /home/electric/.wine/drive_c/Program Files
bash: cd: /home/electric/.wine/drive_c/Program: No such file or directory
electric@XPS-Laptop:~/.wine/drive_c$ 

```

---

### Post by pmlxuser on 2008-07-13
have you tried gksudo or sudo with your commands

ie gksudo cd ~/.wine/drive_c/ blah bah

---

### Post by mali2297 on 2008-07-13
Either wrap the entire filename in quotes:
```

cd "/home/electric/.wine/drive_c/Program Files"

```
or put a backslash before the space:
```

cd /home/electric/.wine/drive_c/Program\ Files

```

---

### Post by upchucky on 2008-07-13
Thank you very much, putting entire command in the quotes worked.

---

