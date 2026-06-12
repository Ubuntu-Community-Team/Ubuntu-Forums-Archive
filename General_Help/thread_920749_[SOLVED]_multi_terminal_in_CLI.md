---
title: "[SOLVED] multi terminal in CLI"
date: 2008-09-15
forum: General Help
---

### Post by amin_inb on 2008-09-15
Hi

I am interest if there is a way to run two terminal at same time
on two columns (on for work other for running htop,..)

I know it is possible to do so on Desktops(Gnome, kde,..) with konsole,...

but I want to do so on CLI (I can't install any desktop on this server)

---

### Post by Dr Small on 2008-09-15
> **amin_inb said:**
> Hi

I am interest if there is a way to run two terminal at same time
on two columns (on for work other for running htop,..)

I know it is possible to do so on Desktops(Gnome, kde,..) with konsole,...

but I want to do so on CLI (I can't install any desktop on this server)
Use screen. You can split the screen, with screen, also.

---

### Post by bingoUV on 2008-09-15
By default there are 6 CLI terminals that you reach by Alt-F1, to Alt-F6. So you have 6 terminals there.

The screen option suggested by Dr Small is great. See
```

man screen

```

---

### Post by amin_inb on 2008-09-16
both of method work for switch between screens but  what I want is to have 2 shell in one screen 

I want 2 shell in 2 columns in one screen, one for htop and other for my program, so I can check cpu,.. while checking program status

---

### Post by niteshifter on 2008-09-16
Hi,

Screen will do what you want - but split horizontally. See [this page]("http://www.linuxforums.org/applications/the_screen_program.html") for detailed instructions. 

Quote from the relevant section on that page:
> The usefulness of this is obvious. I'll sometimes use it when installing a system where I haven't yet installed X, or don't plan to install X.

---

### Post by amin_inb on 2008-09-16
> **niteshifter said:**
> Hi,

Screen will do what you want - but split horizontally. See [this page]("http://www.linuxforums.org/applications/the_screen_program.html") for detailed instructions. 

Quote from the relevant section on that page:

wonderful! thanks

here is my sample for ~/.screenrc to run htop on top and below for work!
+++++++++++++++++++
startup_message off
split
screen -t "System monitor" 0 htop
resize 4
focus
screen -t Shell
++++++++++++++++

---

