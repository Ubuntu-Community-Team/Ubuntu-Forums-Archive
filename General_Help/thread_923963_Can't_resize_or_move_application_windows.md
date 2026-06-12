---
title: "Can't resize or move application windows"
date: 2008-09-18
forum: General Help
---

### Post by chipw on 2008-09-18
I have a really strange problem - I can't move or resize my applications windows. If I click the maximize button the top title bar disappears above the top of the screen, then I have to press alt-f10 (or alt-f9, I don't recall which). I right-click on the title bar and click on the option to resize or move and neither works. 

Is this something set up wrong in my Advanced Desktop Effects settings (Compiz Mgr)?

---

### Post by tuxxy on 2008-09-19
Are you using emerald, maybe you could try starting emerald again

```
emerald --replace
```

---

### Post by chipw on 2008-09-19
> **tuxxy said:**
> Are you using emerald, maybe you could try starting emerald again

```
emerald --replace
```

Not using emerald, don't even know what that is, but it is definitely not installed.

---

### Post by anotherdisciple on 2008-09-19
hmmm... did you put a tick beside "window decorations" in compiz?

Try this instead of the emerald command:

```
gtk-window-decorator --replace &
```

---

### Post by chipw on 2008-09-19
> **anotherdisciple said:**
> hmmm... did you put a tick beside "window decorations" in compiz?

Try this instead of the emerald command:

```
gtk-window-decorator --replace &
```

When I use that command I get this -
```
chip@ubuntu:~$ sudo gtk-window-decorator --replace &
[1] 32312
chip@ubuntu:~$ 

[1]+  Stopped                 sudo gtk-window-decorator --replace

```
Even pop-up windows within firefox have to top bar, or even a line across the bottom of the window. Really weird.

---

### Post by chipw on 2008-09-19
I don't know what's going on with this stuff, but all of a sudden my windows are all appearing fine. We'll see how long that lasts...

---

