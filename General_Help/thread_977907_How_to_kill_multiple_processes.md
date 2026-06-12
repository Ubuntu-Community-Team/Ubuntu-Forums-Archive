---
title: "How to kill multiple processes?"
date: 2008-11-10
forum: General Help
---

### Post by Neodynamics on 2008-11-10
I want to reclaim some of my RAM for gaming. (The Ram otherwise claimed by other processes.) I'm trying to kill all unnecessary processes, and was wondering how I could go about killing all of the processes that I don't need quickly, such as keyboard shortcut, and if there is, is there also a command I could use to open them up as quickly also?

Thanks,

---

### Post by geirha on 2008-11-10
One thing you can do is create a .desktop-file in /usr/share/xsessions/ that executes the game. After a restart of gdm, you should be able to choose your game from the login-screen, and run the game instead of gnome. That of course means there will be no window manager, so you can't start other programs, use alt+tab resize/move windows etc. There may be other side effects too, but it's worth a try. Once you exit the game, you'll be taken back to the login-screen.

Note that you can't use arguments in the .desktop-file, so if the game requires arguments to be passed, you need to create a script to run it.

sample.desktop
```

[Desktop Entry]
Encoding=UTF-8
Name=Game title
Comment=Starts the game without a window manager
Exec=/path/to/game
Icon=
Type=Application

```

---

### Post by Sam on 2008-11-10
I second that. This is the best way to run games on linux.

---

### Post by Neodynamics on 2008-11-10
Actually, I like the sound of this, since I will really be doing nothing but the game. Thanks guys, I appreciate it.

---

