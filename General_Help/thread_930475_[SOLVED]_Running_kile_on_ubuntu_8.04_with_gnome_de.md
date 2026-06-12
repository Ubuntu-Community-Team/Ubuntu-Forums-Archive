---
title: "[SOLVED] Running kile on ubuntu 8.04 with gnome desktop"
date: 2008-09-26
forum: General Help
---

### Post by byulent on 2008-09-26
I am a new user of linux and ubuntu. I have a little problem with kile. Whenever I try to run it directly from the Applications->Office->Kile menu, the following warning message appears:

" There was an error setting up inter-process communications for KDE. The message returned by system was: could not open network socket
please check that the "dcopserver" program is running "

On the other hand, when I run kile on a terminal with the command "sudo kile" it works but at the terminal there is an warning message:

" kbuildsycoca running...
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kile: ERROR: Could not create symlink: /home/bulent/.lyx/lyxpipe.in --> /home/bulent/.kde/tmp-bulent-laptop/kileYq8tLB/.lyx/lyxpipe.in
kile: ERROR: Could not create symlink: /home/bulent/.lyx/lyxpipe.out --> /home/bulent/.kde/tmp-bulent-laptop/kileYq8tLB/.lyx/lyxpipe.out
kdecore (KProcess): WARNING: _attachPty() 13 "

My question is how can I make ubuntu run kile directly from the desktop menu?

Thank you

---

### Post by y-lee on 2008-09-26
Open a terminal and type

```
sudo chown -Rc user:user /home/user/.kde*
```

where "user" is your username. And of course enter your password.

> when I run kile on a terminal with the command "sudo kile" it works but at the terminal there is an warning message:

There is a good chance the command sudo kile caused your problem, it is not a good idea to open GUI applications with sudo. Use gksudo kile instead.

---

### Post by byulent on 2008-09-26
Thank you, the problem was resolved.

---

### Post by y-lee on 2008-09-26
Hey that is great :) and I am glad it wasn't some more complex problem. you can mark this as solved now if you will, it makes the forums easier to use for those of us trying to help. (click on thread tools above to do that).

---

