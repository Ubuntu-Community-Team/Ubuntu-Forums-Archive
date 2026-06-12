---
title: "how to copy all texts in kconsole?"
date: 2008-07-16
forum: General Help
---

### Post by firsttimeuser on 2008-07-16
This drives me crazy now, I use kconsole to ssh into routers and every once in a while I Need copy all the "show run" output to somewhere else. I am getting tried of going to the top of the session and selecting from the first line and dragging all the way down. ](*,)](*,)](*,)](*,)](*,)](*,)

Do you guys know if I can do something under kconsole to select all texts? I really miss the ctrl+a, ctrl+c options.

thanks

---

### Post by KeyserSoze93 on 2008-07-17
just select all the text, open up another app like gedit, and press Shift+insert, it will work like ctrl-c, ctrl-v in windows.

---

### Post by firsttimeuser on 2008-07-17
the question is how can I select ALL the text? there is no "select-all" option, and I need left click and drag mouse all the way from top to bottom, and often go through several pages.

> **KeyserSoze93 said:**
> just select all the text, open up another app like gedit, and press Shift+insert, it will work like ctrl-c, ctrl-v in windows.

---

### Post by jocko on 2008-07-17
I'm not sure if this will help you, but it is possible to divert output from a command.
So this command:
```
glxgears > ~/test.txt
```
Prints the output from glxgears in the file ~/test.txt instead of in the terminal.
I don't think it works with every command, though...

---

