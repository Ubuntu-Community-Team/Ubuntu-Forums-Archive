---
title: "Disappearing Toolbar?"
date: 2008-11-28
forum: General Help
---

### Post by Enigmatus on 2008-11-28
A friend running Xubuntu 8.04 has just called me with the following problem:

After having to reboot Xubuntu following a system 'freeze', the top toolbar has seemingly disappeared. How exactly does she remedy this?

Thank you in advance for your assistance.

---

### Post by mali2297 on 2008-11-28
If she lost both panels, then she can probably get them back by launching the run dialog (alt+f2) and typing
```

xfce4-panel

```

If it's only one of the panels, then she can try resetting the configuration by removing the (hidden) directories **~/.config/xfce4/panel** and **~/.cache**, and restart. Alternatively, she can create a new panel via *Settings Manager -> Panel* and then add the items manually (right-click on the new panel).

---

### Post by St Nabi on 2009-10-15
Hi Martin, It was the bottom bar that I lost. It was the one that showed that i had four desktops and i could see which desktop had what on them irrespective of which desktop I went on. I managed to add a new toolbar at the bottom and even managed to get the four desktops displayed but when I scroll between them it does not show me if I have anything open on any of them...

---

### Post by mali2297 on 2009-10-15
> **St Nabi said:**
> Hi Martin, It was the bottom bar that I lost. It was the one that showed that i had four desktops and i could see which desktop had what on them irrespective of which desktop I went on. I managed to add a new toolbar at the bottom and even managed to get the four desktops displayed but when I scroll between them it does not show me if I have anything open on any of them...

Might you have installed Compiz (desktop effects)?

Check that you use the default window manager. In a terminal window, type
```

pgrep xfwm4

```
If it shows a number then the default wm is running. Otherwise, if there is no output, then you are running some other wm or none at all.

---

