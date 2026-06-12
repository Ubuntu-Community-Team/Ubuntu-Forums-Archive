---
title: "Gnome-do froze the whole system"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by elliotn on 2009-03-27
I was installing Gnome-do and guess what happend? When the parkages needed was being installed 1-6. It installed the parkages and stuck at 6 of 6, which is the last parkage at 78% and the whole system came into a stand still, it frooze and had to unplug the pc to restart in, then I tryd again and the same thing happened. What was that

---

### Post by yeats on 2009-03-27
Next time that happens, do Ctrl-Alt-F1, which will allow you to login to a plain-text terminal, or Ctrl-Alt-Backspace, which will restart the X server.  Sounds like at this point you've got at least one broken package.  If you're unsure what to do, post some details here and maybe someone can talk you through a solution.

---

### Post by elliotn on 2009-03-27
What should i post as the pc doesnt give any error, it just stop at parkage 6 of 6 with the last parkage which is 658kb was at 78%, and the system frooze and nothing could work

---

### Post by yeats on 2009-03-27
Synaptic is not going to give you errors (unless you do "show terminal" if that's an option).  You'll want to do Ctrl-Alt-F1 (or restart X by doing Ctrl-Alt-Backspace, then open a terminal, which will allow copy/paste and probably won't freeze your x-server)

```
sudo apt-get get update
```

There should be some error output there...

---

