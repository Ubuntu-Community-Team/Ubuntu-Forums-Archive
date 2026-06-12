---
title: "Opening gcc"
date: 2008-07-27
forum: General Help
---

### Post by Reversik on 2008-07-27
Hello I'm a newbie to linux recently installed kubuntu and I want to open up gcc the c and c++ compiler but I don't know really how. I'm trying to learn programming and found out a bit how to do that and I needed to open that program it's installed on the computer I know that because I looked it up in Adept Manager. If anyone could help that'd be much appreciated.

---

### Post by txcrackers on 2008-07-27
Compilers, in general, do not have GUI interfaces, so you have to invoke them from a command-line.

---

### Post by braddcadd on 2008-07-27
> **Reversik said:**
> I want to open up gcc the c and c++ compiler but I don't know really how

The gcc compiler is basically a command line tool.  Here is a quick CLI tutorial: [http://ubuntuforums.org/showthread.php?t=854014](http://ubuntuforums.org/showthread.php?t=854014)

If you like lightweight text editors, Geany is a good one.  It is GUI based (although I think it requires gnome graphical libraries which you may not have installed yet, it will work but just take hard drive space).  Geany has a single button for compilation.  It runs the following in a terminal for you:
```

gcc -Wall -c "current_open_file.c"

```

Here are a couple more in-depth (but still starter) tutorials:
[http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html](http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html)
[http://www.tlug.org.za/wiki/index.php/Gcc](http://www.tlug.org.za/wiki/index.php/Gcc)

Good luck!

---

