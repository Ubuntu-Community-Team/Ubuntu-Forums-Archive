---
title: "[SOLVED] what does this code do?"
date: 2008-07-11
forum: General Help
---

### Post by phantomjoker on 2008-07-11
Hi can you tell me what this code does?

> glxinfo | grep "render"

(_[COLOR="Red"]if you don't know then don't try it[/COLOR]_) is it [FONT="Arial Black"]dangerous?[/FONT]

thanks

---

### Post by dracayr on 2008-07-11
it's not dangerous, it just outputs info about your rendering

dracayr

---

### Post by rbc on 2008-07-11
It's saying, do the glxinfo command (see the man page for more), then | (pipe) the results through grep, looking for the word "render"

---

### Post by MasterXandrex on 2008-07-11
glxinfo - shows information about the OpenGL and GLX imple&#8208;mentations running on a given X display -- in other words video card and display info

| - pipe - takes the output of one command and runs it through another

grep - searches for a given string and returns any line containing it
render - the given string


Xan

---

### Post by Dr Small on 2008-07-11
Use 'man command' against each command, read the manual, study it, and then you should determine what it will do when you execute it. It is very self-explanitory.

---

