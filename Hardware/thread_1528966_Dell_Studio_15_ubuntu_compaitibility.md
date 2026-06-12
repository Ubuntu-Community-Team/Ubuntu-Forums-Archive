---
title: "Dell Studio 15 ubuntu compaitibility?"
date: 2010-07-11
forum: Hardware
---

### Post by Zorgoth on 2010-07-11
I ordered a Dell Studio 15 recently.  Are there any Ubuntu compatibility issues with this machine?

(ordered core i7-quad, ati 5470)

---

### Post by Zorgoth on 2010-07-26
In case anyone else is ever interested, this machine works great; there are a few things to note though:

At the time I am writing this, you need to get the very latest drivers from the ATI website rather than the drivers from "Hardware Drivers" to get OpenGL 4.0 working properly.  I also have some weird issue where LIBGL_ALWAYS_INDIRECT is set no matter what launches the process; this is annoying but bearable since I can do something like:

bash -c "unset LIBGL_ALWAYS_INDIRECT && my_command" and then I'm fine.

Once I have all that set up, the graphics work magnificently; I can play all my 3D games under wine like this.

Another thing to note is that the function keys are set up stupidly to begin with; pressing F2 or even Alt-F2 will cause the wireless to toggle, and you have to press, say, Alt-Fn-F2 to get the normal functionality.  There is a BIOS setting in "Advanced" that will switch this to a sensible configuration (e.g. Fn-F2 toggles wireless)

Also, there is no pause/break key...

---

