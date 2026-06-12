---
title: "how do I move files into a root directory"
date: 2008-11-27
forum: General Help
---

### Post by vistadude on 2008-11-27
how do I move files into a root directory?

---

### Post by whitethorn on 2008-11-27
you can either use

```
sudo mv file /root/ ...
```

or you can press alt+F2 and then type gksu nautilus  Type in your password and now you can copy/move and paste.  Just be careful what you move around.

---

### Post by snova on 2008-11-27
You don't, because I can guarantee it doesn't belong there. Stick with your home directory.

---

### Post by vistadude on 2008-11-27
just to let u no, by root directory i don't mean the actual root directory, I mean a directory that is set so that only the root user owns it

---

### Post by snova on 2008-11-27
Ah, /root? Wasn't sure. Although you probably still shouldn't be messing there... why?

whitethorn answered the *how* quite well, though.

---

### Post by vistadude on 2008-11-27
well to be pacific I am trying to install a theme and plugins for AMS, and from my understanding I need to add the folders into the theme directory were the program is installed. And it dose not let me place them in that directory because i don't have promising.

---

### Post by mgmiller on 2008-11-27
Ah, vistadude, we meet again....

The easiest way to get root access to your entire file system is to run the file browser, called nautilus, as root.

in terminal, enter the following command:
```
gksu nautilus 
```Notice we are using gksu instead of sudo because we are trying to run a graphical progam as root.  It will work 99% of the time if you try the command as sudo, but that 1% is nasty, so use gksu for graphical commands.

All that being said, BE VERY VERY CAREFUL WHILE BROWSING AS ROOT!!!

I can't stress that enough.  You now have the power to really frak your system, so be totally sure of what you are moving where.


Have fun, but BE CAREFUL...

---

### Post by vistadude on 2008-11-27
sweet, that works perfect, and I'll be as care full as i can

---

### Post by mgmiller on 2008-11-27
Welcome to Ubuntu, we aim to please......

If you would like to "officially" thank some one for their help, look in the post that you found helpful and in the lower right corner next to the quote button is a little gold medal icon.  Just click that and the person gets a "Thank You".  

These are quite valuable, as they are suitable for framing or wrapping fish. :lolflag:

---

