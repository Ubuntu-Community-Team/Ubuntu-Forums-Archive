---
title: "Save Terminal session"
date: 2008-10-11
forum: General Help
---

### Post by vibra on 2008-10-11
Hello guys,

I wanna know if there is any program or plugin for a Terminal, that could allow me save its state. 

I work a lot with multi terminal at same time. So,when i restart the computer, i want open my past sessions and locations where i'm working. 

Something similar of what happens in firefox.

---

### Post by Sam on 2008-10-11
Use [screen](apt://screen).

Once installed, run in a terminal:
```
screen
```

Do whatever you want, then hit Ctrl-A then D to detach from screen.

Later, use:
```
screen -r
```
To reattach the previous session.

Get more info with:
```
man screen
```

---

### Post by vibra on 2008-10-11
thanks sam, but its not exactly what i'm trying to find.

I find an older Thread with the same issue: [http://ubuntuforums.org/showthread.php?t=791504](http://ubuntuforums.org/showthread.php?t=791504)

but i remain with some problems. in this moment i can save the sessions, but, the ssh terminal opened was lost.. probably, there is nothing we can do because now looks a security issue.

---

### Post by darth_geekboy on 2009-09-09
i've been wondering about this problem also.  i'm coming in from Fedora, and eventually, i found ubuntu to be more attractive.

i've partially figured out this problem.  simply install "Konsole".  for some reason, the gnome environment in ubuntu, doesn't want to save multiple gnome-terminals.  however, it can save multiple "Konsole" terminals.

Fedora was able to save all your gnome-terminals in multiple workspaces, but not ubuntu, and this is the one thing that annoys me about it.

---

### Post by lildigiman on 2009-09-09
Hahaha - you can Have My computer - my problem is My sessions in Ubuntu Keep changing on me. I boot one time, and I get an old session from like 2 boots ago. Or I boot up, and its the most recent. I don't understand WHY though.

---

