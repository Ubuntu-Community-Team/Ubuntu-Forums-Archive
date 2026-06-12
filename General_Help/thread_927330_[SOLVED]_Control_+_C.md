---
title: "[SOLVED] Control + C"
date: 2008-09-22
forum: General Help
---

### Post by matt79 on 2008-09-22
OK on a windows computer control + c with do the copy function.
On my ubuntu machine it does not work. The cut and paste do. I have tried the copy function on another ubuntu computer and it works, so something must have gotten messed up with I was "playing" around on my computer. Does anyone know how to correct this?

I just found out that control + c moves my mouse pointer to the center of the screen.

---

### Post by Sinkingships7 on 2008-09-22
Not sure what could have went wrong, but you can try going to "System -> Preferences -> Keyboard Shortcuts" and try to diagnose the problem.

---

### Post by matt79 on 2008-09-22
> **Sinkingships7 said:**
> Not sure what could have went wrong, but you can try going to "System -> Preferences -> Keyboard Shortcuts" and try to diagnose the problem.

I did but I could not find anything that helped. I thought I could at least set it back to copy but there is no option for that.

---

### Post by mb_webguy on 2008-09-22
> I just found out that control + c moves my mouse pointer to the center of the screen.Are you using Compiz effects?  I seem to recall a plugin that does that...

---

### Post by Dr Small on 2008-09-22
Also, if you are trying this in a terminal, CTRL + C kills the program. To copy in the terminal, use CTRL + SHIFT + C

---

### Post by matt79 on 2008-09-22
I found the problem under enhanced zoom desktop. The mouse behavior was set to control + c. I remembered that I set up emerald and some other stuff when I first set the box up and since it never copied I thought I would to back to when it started. :-)

---

### Post by pansz on 2008-09-22
Does your "ubuntu" promises it will have the same behavior as Windows? unlikely.

For Unix and Linux tradition, Ctrl-C is reserved for kill the program, and *never* used for copy & paste. So this combination will never work in ubuntu.

---

### Post by Sinkingships7 on 2008-09-22
> **pansz said:**
> Does your "ubuntu" promises it will have the same behavior as Windows? unlikely.

For Unix and Linux tradition, Ctrl-C is reserved for kill the program, and *never* used for copy & paste. So this combination will never work in ubuntu.

Uh huh. If you say so.

---

### Post by mb_webguy on 2008-09-22
> **pansz said:**
> Does your "ubuntu" promises it will have the same behavior as Windows? unlikely.

For Unix and Linux tradition, Ctrl-C is reserved for kill the program, and *never* used for copy & paste. So this combination will never work in ubuntu.

Um... except that it *does*.  Ctrl-C kills a process in the terminal, but it's the Copy shortcut in most GUI applications, including Nautilus and every other GUI file manager I've ever used for Linux.

---

### Post by matt79 on 2008-09-22
For me it works as a copy on the GUI.

---

