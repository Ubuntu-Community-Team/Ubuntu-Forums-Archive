---
title: "mplayer captures mouse clicks"
date: 2009-02-10
forum: Hardware
---

### Post by attentat on 2009-02-10
So I have two computers, one desktop and one laptop. The laptop uses Ubuntu and the desktop uses Kubuntu with a Microsoft wireless mous. I frequently use the laptop to ssh into the desktop to play movies (since the desktop is hooked up to my tv) in mplayer from the command line. But there's frequently this bizarre problem I can't figure out where the mouse on the desktop stops functioning properly. For whatever reason the mouse clicks get captured by mplayer and I (sometimes) get errors in my terminal on the laptop saying that the mouse clicks don't have any bindings. Meanwhile, I can't really do much of anything on the desktop. The problem usually persists even after mplayer is closed. It's easily fixed by restarting X or the whole computer, but that's not always something I want to bother with.

I haven't tried a whole lot because I'm not really sure what to try. I ran "modprobe -l *mouse*" and then ran "modprobe -r" with each driver (I don't know which one) before running "modprobe" on it again. Nothing. 

Any ideas?

---

