---
title: "Where can I find the source code for ubuntu's task bar/top panel?"
date: 2008-09-09
forum: General Help
---

### Post by libird on 2008-09-09
Hi all,
  I want to understanding the implimentation of the task bar or top panel. 
  Is there any one can tell me where to find the source code of the task bar / top panel of ubuntu?

---

### Post by Mister.Vash on 2008-09-09
I believe you are talking about Gnome Panel?  You can download the source used in ubuntu here:
[http://packages.ubuntu.com/source/hardy/gnome-panel](http://packages.ubuntu.com/source/hardy/gnome-panel)

---

### Post by libird on 2008-09-10
> **Mister.Vash said:**
> I believe you are talking about Gnome Panel?  You can download the source used in ubuntu here:
[http://packages.ubuntu.com/source/hardy/gnome-panel](http://packages.ubuntu.com/source/hardy/gnome-panel)


thanks for the help, i have downloaded the source. 
Now ,there's another problem: i can't found the source code for the "Quit button" applet which is in the right of the top panel.
Does anybody can tell me where to find it?

---

### Post by libird on 2008-09-11
> **libird said:**
> thanks for the help, i have downloaded the source. 
Now ,there's another problem: i can't found the source code for the "Quit button" applet which is in the right of the top panel.
Does anybody can tell me where to find it?

Does anybody knows it?

---

### Post by rsambuca on 2008-09-11
How about this simple command?

```
gnome-session-save --kill
```

---

