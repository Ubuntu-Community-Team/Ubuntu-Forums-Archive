---
title: "Can't navigate to 2 specific folders from terminal"
date: 2008-08-24
forum: General Help
---

### Post by go7Ul1ai on 2008-08-24
Hello,

I can't seem to navigate to 2 folders through the terminal, If I rename them to something else I can access them, but I want them named how they are. I even used Sudo Nautilus to give the folders full permissions but still no luck.

Here's what I try, and get (copied from terminal):
lee@lee-laptop:~$ cd Documents
lee@lee-laptop:~/Documents$ cd Programming
lee@lee-laptop:~/Documents/Programming$ cd Games
lee@lee-laptop:~/Documents/Programming/Games$ ls
Lee Invaders v0.1  Lee Invaders v0.2  test.py~
lee@lee-laptop:~/Documents/Programming/Games$ cd Lee Invaders v0.1
bash: cd: Lee: No such file or directory
lee@lee-laptop:~/Documents/Programming/Games$ 

If anyone can help, that would be great,

Lee

---

### Post by go7Ul1ai on 2008-08-24
Hello there, anyone?

---

### Post by mssever on 2008-08-24
Either:

[LIST]
[*]Precede spaces and special characters with a \
[*]surround the directory name in quotes; or
[*]use tab completion (google bash tab completion)
[/LIST]

---

### Post by sstusick on 2008-08-24
If the directory/file names have a space between words, you need to wrap it in quotes.

---

### Post by wannadumpwindows on 2008-08-24
And for future reference, you don't need to bump your threads in an hour.

Give people a chance to find your thread, so they can help you out.

This is a forum, if you need more timely assistance, use the irc channels.

---

### Post by mssever on 2008-08-24
> **wannadumpwindows said:**
> And for future reference, you don't need to bump your threads in an hour.
In fact, bumping threads will prevent the unanswered posts team from finding them (in many cases), so it's best to wait at least a day between bumps.

---

