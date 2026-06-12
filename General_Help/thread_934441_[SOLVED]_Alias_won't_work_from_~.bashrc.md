---
title: "[SOLVED] Alias won't work from ~/.bashrc"
date: 2008-09-30
forum: General Help
---

### Post by Sugi on 2008-09-30
I tried tweaking my ~/.bashrc and the alias I added isn't working.

```
~/.bashrc
# some more ls aliases
alias scb='sh /home/sugi/starcraft_box'

```
When i type scb, i get this:
```
$ scb
bash: /sh: No such file or directory
```

My bash file:
```
#!/bin/bash
cd /home/sugi/.wine/drive_c/Program\ Files/Starcraft/
env WINEPREFIX="/home/sugi/.wine/" nice -20 wine explorer /desktop=StarCraft,640x480 "C:\Program Files\StarCraft\StarCraft.exe"
```
The bash file does work if i input into the terminal

What am I doing wrong?

Thanks,
Sugi

---

### Post by karlr42 on 2008-09-30
Maybe try replacing sh in the alias with /bin/sh  ?
Your code works for me in my bashrc, so I don't know what the problem is.

---

### Post by Nepherte on 2008-09-30
Did you open up a new terminal before you entered that command (or relogged in for user-wide effect)? Did you check that it is to correct path to the file?

---

### Post by Sugi on 2008-09-30
> **karlr42 said:**
> Maybe try replacing sh in the alias with /bin/sh  ?
Your code works for me in my bashrc, so I don't know what the problem is.

Prefect.  /bin/sh worked :D

Thanks,
Sugi

---

### Post by Sugi on 2008-09-30
How do I make sure linux reads the new saved ~/.bashrc?  What's the command I have to in?  Or I have to logout everytime I make a change to the .bashrc.

Sugi

---

### Post by karlr42 on 2008-09-30
Yeah, I'd say log out and in again, that restarts  bash

---

### Post by Sugi on 2008-09-30
There's some command for it, but I couldn't find it.  I keep searching google.

---

### Post by mbeach on 2008-09-30
try
```
source ~/.bashrc
```
or just:
```
bash
```

---

### Post by Sugi on 2008-10-02
> **mbeach said:**
> try
```
source ~/.bashrc
```
Awesome, that worked. Thanks :D

---

