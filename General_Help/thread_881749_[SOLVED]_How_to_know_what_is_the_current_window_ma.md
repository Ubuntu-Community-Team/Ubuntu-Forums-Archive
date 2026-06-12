---
title: "[SOLVED] How to know what is the current window manager?"
date: 2008-08-06
forum: General Help
---

### Post by Pidgin on 2008-08-06
I know it must be a silly question. But I'm a Linux newbie, and I cannot find any information about it through Google. How can I find out what is the current window manager that is running?

---

### Post by kihjin on 2008-08-06
Unless you've changed your window manager, you will still have the same manager that was installed by default when you setup ubuntu.

If you're using Ubuntu (you'll see a Ubuntu logo when you log-in) then you using Gnome.

If it is Kubuntu, you are using KDE

If it is Xubuntu, you are using XFCE - this also qualifies you as being super awesome! Not that there's anything bad about the other two...

Although to be fair, Gnome, KDE, and XFCE aren't entirely Window Managers, they are desktop environments. Each of them comes packaged with their own specialized Window Manager. XFCE's manager is called xfwm4, for instance. You might be able to find it in your computer's process list.

Good luck

---

### Post by tuxxy on 2008-08-06
Window manager should either be metacity by default a lot of people like emerald manager also, this is the one to give you vista like aero theme if it helps.

---

### Post by Pidgin on 2008-08-06
Oh, thanks.
I think I mean exactly the window manager, not the desktop manager.
I have accidentally run the command "metacity --replace" from the terminal. I hear that metacity is a window manager, and by running that command metacity would be the current window manager. So I want to know what is the original window manager, ie. the default window manager of a fresh Ubuntu 8.04.1 installation.

---

### Post by tuxxy on 2008-08-06
yes Metacity is the default, if you want a bit more of a eye candy manager try Emerald

```
sudo apt-get install emerald
```

Now run the command to replace metacity with emerald

```
emerald --replace
```

You can store the command at system > prefs > session to allow emerald to be run at bootup and you not have to reenter the command every time.

---

### Post by billgoldberg on 2008-08-06
> **Pidgin said:**
> Oh, thanks.
I think I mean exactly the window manager, not the desktop manager.
I have accidentally run the command "metacity --replace" from the terminal. I hear that metacity is a window manager, and by running that command metacity would be the current window manager. So I want to know what is the original window manager, ie. the default window manager of a fresh Ubuntu 8.04.1 installation.

Metacity is the default WM.

Unless you installed emerald and use it, then Emerald is your window manager.

Run emerald --replace to start it.

---

### Post by billgoldberg on 2008-08-06
> **tuxxy said:**
> yes Metacity is the default, if you want a bit more of a eye candy manager try Emerald

```
sudo apt-get install emerald
```

Now run the command to replace metacity with emerald

```
emerald --replace
```

You can store the command at system > prefs > session to allow emerald to be run at bootup and you not have to reenter the command every time.

Be advised that you'll need a compositing manager (compiz fusion) running for this WM to work.

---

### Post by tuxxy on 2008-08-06
ahh yes, make sure you enable the desktop effects at system > prefs > appearance and also download ccsm to manage your effects if you didnt already

```
sudo apt-get install ccsm
```

---

