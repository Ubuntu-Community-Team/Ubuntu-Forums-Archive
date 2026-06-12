---
title: "Bluetooth mouse latency with OpenGL"
date: 2010-03-30
forum: Hardware
---

### Post by perilandmishap on 2010-03-30
My bluetooth mouse is jittery and laggy to the point of being unusable whenever I open an OpenGL application such as glxgears or tetris (or wow in wine).  It works fine the rest of the time, but I got it for gaming...

I've tried adding the blueman ppa and updating to the latest version, but that hasn't resolved the problem.


Any ideas on what might be causing this?

Thanks!

---

### Post by Fafler on 2010-03-30
High CPU usage? Bluetooth recievers are usually USB devices and as such prone to lack caused by system load. Open a terminal and run top. Or if the OpenGL application runs in fullscreen, ctrl+alt+f1 to the console, login and top or ssh from another machine.

I use bluetooth mice with two of my computers and don't have any such problems.

---

### Post by perilandmishap on 2010-03-30
I thought it was just a load issue at first, but if I say open 3 browser windows playing flash and Netbeans all at the same time it pushes my CPU to about 60% and doesn't cause the issue.  Meanwhile running glxgears causes very little load on my machine but does.  

I am certain that this is an issue with openGL not load.

Thanks for the response though, any other ideas?

---

### Post by enbaeza on 2010-04-01
Did you ever find out how to load OpenGL? I have installed a lot of packages that concerns OpenGL and still getting the same error, This system does not support OpenGL.

---

