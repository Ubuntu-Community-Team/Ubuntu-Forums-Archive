---
title: "[SOLVED] Is there anything like Ctrl alt delete for ubuntu?"
date: 2008-08-26
forum: General Help
---

### Post by dragos240 on 2008-08-26
I have some programs some times that wont go away. Any way i can get something up to help me with that >.<

EDIT: Solved. I found out ubuntu's system monitor. :)

---

### Post by y@w on 2008-08-26
Ctrl-Alt-Backspace will restart X if you get into a bind. Otherwise, you can use Ctrl-Alt-F1 through F6 if you need to get to a virtual terminal to kill a run-away application. Then Ctrl-Alt-F7 will bring you back to X.

---

### Post by dragos240 on 2008-08-26
> **y@w said:**
> Ctrl-Alt-Backspace will restart X if you get into a bind. Otherwise, you can use Ctrl-Alt-F1 through F6 if you need to get to a virtual terminal to kill a run-away application. Then Ctrl-Alt-F7 will bring you back to X.
Thanks

---

### Post by anotherdisciple on 2008-08-26
Just a note... even though this is solved...

Try running xkill like this:

Hit Alt+F2 then type
```
xkill
```
and hit enter.

That will change your cursor to an x... then you just click on the window that won't close. I find that to be easier than opening a system monitor and finding the program that isn't working, but that's just me.

---

