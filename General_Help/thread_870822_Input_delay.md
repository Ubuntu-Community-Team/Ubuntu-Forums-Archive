---
title: "Input delay"
date: 2008-07-26
forum: General Help
---

### Post by EXetoC on 2008-07-26
Hello. I got this problem in some games. The faster i move the mouse or the mouse wheel, the longer the mouse and the keyboard events gets queued, resulting in me not being able to do anything until the queued events have been processed. I'm currently running Ubuntu 8.04 and it also happened in Ubuntu 7.10.

There was this strange fix to this that i came up with myself, and the solution was to either play a song or have it on pause in Audacious (using the ALSA driver, which i use in games as well). As strange as this may be, it worked. But then it stopped working all of a sudden, so the current solution is to start a game like this "xinit <path-to-game-executable> $* -- :1 > /dev/null" without already being logged on to a session (which means i have to execute it from one of the virtual consoles (Ctrl+Alt+Function key))

I've also tried to experiment alot with the mouse settings in xorg.conf, but without results. Are there some Ubuntu startup scripts that may cause this? Beacuse it doesn't happen in Xfce only, but in all DE's/WM's.

---

### Post by EXetoC on 2008-07-26
Ok, all of a sudden it works when i start a game in a separate X display even when i'm logged in to a session already. I'm not really sure why it works all of a sudden, but it's not optimal since it's not possible to regain focus of the game once the focus is lost.

---

### Post by EXetoC on 2008-07-28
And sometimes when i spawn an X display when i'm not logged in to a session, the sensitivity ingame slows down at random intervals.

---

### Post by Megatog615 on 2008-07-31
I have the same problem. Perhaps we should open a bug report for this? First we should track down what is causing it.

From what I see it seems to be any SDL-based application that's doing this. All ioQuake3-based games, Enemy Territory: Quake Wars, Osirion, etc are having this problem.

What mouse do you use? I have a Logitech Trackman Wheel:
[img]http://www.atpm.com/11.12/images/trackman-wheel.png[/img]

---

### Post by Megatog615 on 2008-08-01
I've opened a bug report for this problem, as a couple of my friends who use Ubuntu also confirmed this problem as well.

[https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/254045](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/254045)

---

### Post by Thornation on 2008-08-01
Yeah. Got that bug here too. Seems to be something in SDL_GetMouseState(); (or whatever it's called, can't remember). Not sure if this is a bug with the kernel or what.

Mouse is an A4tech Office8k
Kernel:2.6.24-19-rt
Ubuntu version: 8.04

---

### Post by Megatog615 on 2008-08-01
I just asked one of my friends who isn't affected by the bug what kernel he uses. He told me he uses a the generic kernel.

Maybe it has to do with the rt kernels?

---

