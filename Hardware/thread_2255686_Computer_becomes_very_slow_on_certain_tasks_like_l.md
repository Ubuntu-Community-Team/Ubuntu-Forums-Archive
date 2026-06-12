---
title: "Computer becomes very slow on certain tasks like large file transfer or installation"
date: 2014-12-06
forum: Hardware
---

### Post by john135 on 2014-12-06
I apologize if this question has already been asked but I couldn't find anything online.
I recently purchased a new HP computer, HP Pavilion 17 f113dx and installed Ubuntu 14.10 on it. Most of the time it runs fine and is usually very fast, however I noticed that on certain tasks, like large file transfers between the computer and an External HD or installing large programs, the computer becomes very slow and lagging, to the point that I can't really do anything until the said operations is done. After that it goes back to working fine as usual.
It only has happened a few times so far, the last time being when I installed Mathematica (a 2.5GB script file).
My question is whether this is an operating system issue that I can fix, or whether my computer is just not powerful enough to run these kind of operations. Here is a link with my specs:[http://www8.hp.com/h20195/v2/GetDocument.aspx?docname=c04511132](http://www8.hp.com/h20195/v2/GetDocument.aspx?docname=c04511132)
Has anyone else tried this computer with Ubuntu?
If it's the latter, then I can still return it and probably get a better one.
Thanks in advance!!

---

### Post by ibjsb4 on 2014-12-08
IMO, your specs are good.  Try monitoring cpu and ram usage with the processes tab in your system monitor or do it in terminal.
```
top
```
You could also install a less resource demanding desktop on your current install.  I believe this command will work in 14.10.
```
sudo apt-get install gnome-session-flashback
```
Reboot and choose Flashback (metacity) at the login screen by clicking on the icon.

---

