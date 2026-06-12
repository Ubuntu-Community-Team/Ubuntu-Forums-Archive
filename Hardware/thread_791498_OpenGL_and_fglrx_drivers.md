---
title: "OpenGL and fglrx drivers"
date: 2008-05-12
forum: Hardware
---

### Post by heyl1 on 2008-05-12
Hello,

I have an ATI Radeon Xpress 200M 1GP graphics card and now using the fglrx drivers. However, when I try to run an OpenGL app that I've written in C (or an app provided by the lecturers) it does different things. Either the window doesn't pop up, it stays hidden in the task bar. Or it does run but the border with the title is gone, and it doesn't seem to run correctly. Or it doesn't render it properly.

I'm now using Hardy Heron, but it used to work fine on Gutsy, no problems at all.
Because I have an OpenGL project at the moment, it's pretty important that I can get it to work, so I would be really thankful if someone could help me.

Thanks in advance!
Heleen

P.s. I'm a bit of a noob. And I'm on an HP Compaq Presario V5099EA laptop, with 1gb ram, AMD Turion ML-40 processor.
When typing fglrxinfo in terminal I get:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

---

### Post by heyl1 on 2008-05-12
I fixed my own problem :).
First I installed Envyng Core and envyng gtk.
Then I used that to reinstall my ATI drivers.
Then apparently it automatically turns compiz on, well at least the normal visual effects. So I turned it off, and it worked :D.
I then wanted dual monitors. But I noticed it didn't quite work properly, so I turned Metacity Compositing off and it worked (used it for AWN, guess I'll have to be without it for the duration of my project).

So, I haven't got my dual monitors quite working right yet. But it's usable for now, and at least my OpenGL is working! :D

---

