---
title: "xterm auto-completion of old commands"
date: 2008-07-13
forum: General Help
---

### Post by gollum77 on 2008-07-13
Hi,

I am on Ubuntu 8.04. In some other Linux distros like SLES xterm had a default key binding (SHIFT-Up Arrow) which allowed auto-completion of old commands in the bash history. For example say I have executed "ls -la ubuntu" successfully. There on typing "ls" and then using "SHIFT-Up Arrow" would cause "ls -la ubuntu" to show up. Any idea how I can do this on Ubuntu 8.04?

Thanks.

---

### Post by mcduck on 2008-07-14
Try with Ctrl-r.

---

### Post by cariboo on 2008-07-14
You can use the up arrow to scroll through previous commands that you have typed in the terminal. Though it will only work for the session you are in. If you close the terminal you don't have the history anymore.

Jim

---

### Post by justleen on 2008-07-14
actually, the history of your session is kept even if you close it, or reboot..
but: if you have two terminal sessions open, you close them both, then when openening two new ones they wont have separate histories, just the one..

@op:  if your in a bash shell, you should be able to use the up-arrow, 
typing "history" can help as well (you can grep in "history" but then ctrl-r is just as handy..)

---

### Post by CatKiller on 2008-07-14
If you put ```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
``` in your ~/.inputrc file, you can use Page Up and Page Down to complete commands based on your history. If you knew how to describe key combinations (I don't) you could set those aliases to be whatever you were most comfortable with.

---

### Post by gollum77 on 2008-07-14
Ctrl-R really doesn't do the trick. It doesn't let me scroll through the possible commands already in the history. 

I know about the "history" command and the use of up and down arrows to recall them.

What I am looking for is a slight modification. For example typing "ls" and then using "SHIFT+UP Arrow" would in effect allow me to scroll through all past incantations of "ls".

Hope I am being clear :) If not I will gladly clarify.

---

### Post by CatKiller on 2008-07-14
> **gollum77 said:**
> What I am looking for is a slight modification. For example typing "ls" and then using "SHIFT+UP Arrow" would in effect allow me to scroll through all past incantations of "ls".

That's what the modification to your .inputrc will do. I feel really crippled now when I use someone else's computer and it doesn't work.

---

### Post by gollum77 on 2008-07-14
> **CatKiller said:**
> If you put ```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
``` in your ~/.inputrc file, you can use Page Up and Page Down to complete commands based on your history. If you knew how to describe key combinations (I don't) you could set those aliases to be whatever you were most comfortable with.
Yes that's exactly what I am looking for. Adding the following to inputrc:

"\e[1;2B": history-search-forward
"\e[1;2A": history-search-backward

Thank you :)

---

### Post by CatKiller on 2008-07-14
Well, you did better than me at finding out what the escape sequences for Shift-Up and Shift-Down are :)

Don't forget to mark the thread as solved.

---

### Post by VMC on 2008-07-14
> **gollum77 said:**
> Ctrl-R really doesn't do the trick. It doesn't let me scroll through the possible commands already in the history. 

I know about the "history" command and the use of up and down arrows to recall them.

What I am looking for is a slight modification. For example typing "ls" and then using "SHIFT+UP Arrow" would in effect allow me to scroll through all past incantations of "ls".

Hope I am being clear :) If not I will gladly clarify.
try it using :

```
history | less
```

---

