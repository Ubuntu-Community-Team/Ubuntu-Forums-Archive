---
title: "Run xscreensaver on only 1 monitor of dual-head?"
date: 2008-09-17
forum: General Help
---

### Post by 01000111 on 2008-09-17
Greetings all,

I've replaced gnome-screensaver with xscreensaver and it works great.  I have a dual-head setup (2 monitors connected to one video card via 2 vga ports) and want to run the screensaver on just one of the monitors.  

When I attempt to run xscreensaver while its already running, I correctly get the error:

[I]xscreensaver: 13:11:34: already running on display :0.0 (window 0x2c00044)
 from process 6511 (user@host).
xscreensaver: 13:11:34: already running on display :0.0 (window 0x2c00046)
 from process 6511 (user@host).
[/I]

...which seems to indicate that it recognizes the two monitors separately.  How do I tell it to run on only one of them?

Thanks in advance.

Binary-G

---

### Post by northern lights on 2008-09-17
Let it be said that I never used xscreensaver. I don't know whether there might be a GUI option. When manually running it, ```
export DISPLAY=:0 && xscreensaver
```might make that happpen (the respective other monitor'd be 'DISPLAY:=1')

---

### Post by 01000111 on 2008-09-17
> **northern lights said:**
> Let it be said that I never used xscreensaver. I don't know whether there might be a GUI option. When manually running it, ```
export DISPLAY=:0 && xscreensaver
```might make that happpen (the respective other monitor'd be 'DISPLAY:=1')


Thanks, but that didn't work.  When I set it to =:0, it runs on both screens.  When I set it to =:1, it gives the error "Can't open display: :1"...  which, I assume, is because I only have 1 display with multiple windows, not multiple displays.

01000111

---

### Post by northern lights on 2008-09-17
Yep, right.

TwinView is represented as one big display to the OS. My bad.

By using [Devil's Pie]("https://help.ubuntu.com/community/Devilspie") you can set the screen position on which an application should open.

---

