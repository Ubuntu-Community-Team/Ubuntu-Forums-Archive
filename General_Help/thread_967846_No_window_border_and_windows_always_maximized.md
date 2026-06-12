---
title: "No window border and windows always maximized"
date: 2008-11-02
forum: General Help
---

### Post by dubbaluga on 2008-11-02
Hi,

today I installed the Ubuntu 8.10 Desktop Edition for AMD64 on my laptop. I am using XFCE4 as my window manager and therefore installed the "xubuntu-desktop" package. Currently there are two problems:

[LIST]
[*]windows always get maximized and
[*]there is now window border
[/LIST]

I think it has something to do with compiz, which is enabled in gnome by default. Does anybody know, how to get these settings back? This is really annoying because even the little "xf4run" window gets maximized to the size of my current desktop minus the height for the window border (containing the "x" to close the window).

Thx in advance,
  Rainer

---

### Post by dubbaluga on 2008-11-02
... it was the devilspie daemon. Just uninstalled it including its dependencies with aptitude and that's it.

```
sudo aptitude remove devilspie
```

Regards,
  Rainer

---

### Post by revoman3 on 2008-11-03
thanks I have the same problem, just uninstalled it and I hope it works when I reboot :)

EDIT:
Thanks it fixed the problem, my 4 day search for a solution is over! :D
what was that package supposed to do anyway?

---

### Post by KentonS on 2008-11-04
Weird... I'm running DevilsPie (to move my VirtualBox Windows XP Guest window to Desktop 2), and it causes me no problems. (I'm running Ubuntu 7.10, with metacity as my window manager. I completely removed compiz from the system.)

I am, however, experiencing this problem when I create a user, then log in as that user. No windows decorations, plus it takes upwards of two minutes for the network manager (Wicd) and Bluetooth icons to show up on the panel and for me to be able to bring up the screen to let me shut down, log off, etc. (The lack of window decorations and the delay may be two entirely separate and unrelated issues.) I can get window decorations to appear if I bring up a terminal session and issue a "metacity --replace" command, but they disappear as soon as I bring down the terminal sesion.

---

### Post by KentonS on 2008-11-06
Well, it took some digging, but I found the problem. Everything works fine now.

---

