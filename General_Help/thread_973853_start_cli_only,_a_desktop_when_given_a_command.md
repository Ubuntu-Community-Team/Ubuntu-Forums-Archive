---
title: "start cli only, a desktop when given a command"
date: 2008-11-07
forum: General Help
---

### Post by Flybersite on 2008-11-07
Hello

As I'm using Intrepid Ibex as VM on my laptop to act as development server I only have the cli installed

Now, as I'm also intrested to learn more about linux I'm wondering how I can start ubuntu-desktop only when I ask for it with a command.

Can somebody help me out

Thanks in advance

Glenn

---

### Post by DefineByte on 2008-11-07
Well, I'm no expert (don't run away!) but I guess you could install ubuntu-desktop and then remove GDM from start-up using bum (terrible name but probably the easiest to use) or sysv-rc-conf (runs in the terminal). Then you'd just need to type startx from the prompt to get into the desktop.

(hopefully someone will correct me if I'm wrong :D)

---

