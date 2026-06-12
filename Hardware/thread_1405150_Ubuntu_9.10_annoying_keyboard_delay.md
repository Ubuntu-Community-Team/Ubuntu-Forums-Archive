---
title: "Ubuntu 9.10 annoying keyboard delay"
date: 2010-02-12
forum: Hardware
---

### Post by catalin.soare on 2010-02-12
[FONT=Lucida Sans Unicode][SIZE=2]Hi![/SIZE][/FONT][FONT=Lucida Sans Unicode][SIZE=2]

I have a weird keyboard problem ever since Ubuntu 9.10 X64 (all the updates successfully applied but nothing changed). I have an Acer Aspire [/SIZE][/FONT][FONT=Lucida Sans Unicode][SIZE=2]7520G[/SIZE][/FONT][FONT=Lucida Sans Unicode][SIZE=2].
[/SIZE][/FONT][FONT=Lucida Sans Unicode][SIZE=2]
Whenever I type something in a tty, or gnome-terminal, xterm, or anything similar (not in a GUI application like gedit, for example), it seems like the terminal is buffering the characters before displaying them. (I've seen a similar post on [linuxforums]("http://www.linuxquestions.org/questions/linux-kernel-70/keyboard-delay-in-ttys-from-2.6.28-16-generic-to-2.6.31.6-on-ubuntu-9.04-jaunty-769290/"), but nobody answered with a solution to that)

To explain:

[/SIZE][/FONT][INDENT][FONT=Lucida Sans Unicode][SIZE=2] I open xterm, for example, I want to type "apt-get update".[/SIZE][/FONT][FONT=Lucida Sans Unicode][SIZE=2]
A random number of these characters will be buffered by the terminal and will appear only after 1-2 seconds all at once.

Still in any console, I keep a key pressed for 4-5 seconds. A few characters will be displayed normally, but some others will burst only after a 1-2 seconds delay.
[/SIZE][/FONT][/INDENT][SIZE=2][FONT=Lucida Sans Unicode]It is very annoying, since when typing commands in the shell, you also have to think about them, and verify if Tab completed what you needed, so I have to wait..

It's like the IRQs would be different...

On Ubuntu 9.04 X64 everything was perfect.
The problem happens both after I upgrade from 9.04, and after a fresh install of 9.10. Disabling/enabling compiz doesn't help.

Any ideas/suggestions would be greatly appreciated!
Should I try to provide more details?

Thank you for at least reading the whole thread!
[/FONT][/SIZE]

---

### Post by endumenn on 2011-09-28
Have you found out what the problem was?

Some days I have the same problem with Ubuntu 11.04
and xterm.

Other terminal programs that seems not have delay
are gnome-terminal, lxterminal, rxvt

But besides xterm also wterm have delays.

Annoying, I like xterm otherwise, and used it i decades...

---

### Post by davery on 2012-06-04
I've had the same thing since upgrading to (i think) 11.04, 64 bit, now in 12.04.  It's like something is intercepting my keystrokes, and it's too slow to keep up with my typing.  It doesn't affect the ttys, though.  When i type there, everything is smooth.  But in X, i get missed characters all over the place.  Very annoying.

---

