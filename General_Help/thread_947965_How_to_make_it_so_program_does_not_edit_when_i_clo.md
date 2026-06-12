---
title: "How to make it so program does not edit when i close the terminal"
date: 2008-10-14
forum: General Help
---

### Post by josephellengar on 2008-10-14
When I have launched the program with a terminal.  Thanks!
that is, exit

---

### Post by aktiwers on 2008-10-14
Do you mean not "Exit"?

To exit programs from Terminal, press "CTRL+c"
To send a program to background press "CTRL+z"

You can also run your commands in "Alt+F2"

---

### Post by tuxxy on 2008-10-14
Press ALT + F2 and enter the command here, this will run it without temrminal window :)

---

### Post by patrickballeux on 2008-10-14
One utility that is really useful is "screen".  With this, you can start any process in background, then recover that session on a later use...  You can even logout of your session and the process will continue.

Pretty useful on remote ssh connection when you want to start an update and you don't want to stay connected for the process to complete.

Read the man page (man screen) for complete details how to use it.

It is something like:

> screen -m -d yourcommand

and to get it back...

> screen -r 

Good luck!

---

