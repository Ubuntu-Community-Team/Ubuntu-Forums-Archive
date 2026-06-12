---
title: "[SOLVED] A question about cpu affinity"
date: 2008-11-21
forum: General Help
---

### Post by ubuntoooooo on 2008-11-21
I haven't been an Ubuntu user that long, but I think I have tried just about every search I can think of. There's a few threads in your archives, while I follow them it just doesn't work out. (I get an error or something the like)

I've gotten schedtools, I've run cmds such as: 
```
taskset -c 1 -p 9668
taskset -c WolfMP
taskset 0x000001 -p yadayada
```

It's only really for one program that I need this for, it's a game that is un-patched and does not utilize multiple CPU's very well. In windows I had a cmd in NVIDIA Control Panel, threaded optimization on/off/auto. It was close to unplayable without it, kinda like how it is now.

AMD2
Ubuntu 8.04

Any ideas?

---

### Post by ubuntoooooo on 2008-11-21
bump?

---

### Post by ubuntoooooo on 2008-11-22
No takers?

---

### Post by happyhamster on 2008-11-22
- Are you running it with wine? If so, try like this:

taskset 0x00000001 wine program_name.exe

- or (the same):

taskset -c 0 wine program_name.exe

- to get rid of debug-messages:

WINEDEBUG=-all taskset -c 0 wine program_name.exe


Good luck.

---

### Post by ubuntoooooo on 2008-11-22
Danke, solved.

---

