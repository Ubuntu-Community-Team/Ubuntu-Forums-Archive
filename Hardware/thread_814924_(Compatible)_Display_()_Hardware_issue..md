---
title: "(Compatible) Display (?) Hardware issue."
date: 2008-06-01
forum: Hardware
---

### Post by Black Serpent on 2008-06-01
Hello!

Summary:
I have an MSI-built laptop, which seems at first to have a hardware issue, BUT, it works ok under a different operating system.

Here are the details:
The North Bridge is GML965 intel chipset. The graphics card is GMA x3000 or x3100, doesn't matter.
Games (openArena, tumiki fighters, freedroids) run ok, but crash after 3-5 minutes. The crash results in a graphical distortion, and also the following:
complete system freeze (including screen brightness with Fn key).
Ctrl+Alt+Backspace doesn't work
Ctrl+Alt+F1 doesn't work
However, Alt+sysrq+b resets the computer.

I first thought it was a pure hardware problem, since it popped up. These games worked fine in the past and the problem persisted when I reinstalled everything.

Also, I checked glxgears, which did not crash the computer. same as running the games Minimized.

In order to prove that it really is a hardware problem, I would have to show the seller that it also does the same under Win.

And that's exactly the problem - it does not crash under Win.

I checked if it could be due to an update - and no, I took a CD I burnt 2 months ago (Ubuntu 8.04) and ran the games before (and after) the updates. results were the same.
----

Solution:
I've been thinking about compiling the whole thing by myself. There is a chance that it would fix the problem.
What do you think?

---

### Post by Black Serpent on 2008-06-01
[!!! Important !!!]

Apparently, after some further searches,

it seems that COMPIZ caused the problem. by taking it out completey at the Appearance settings, the problem did not return !

Although it looked like a hardware problem, it was not. It is a specific bug that occurs with these devices and installations.

---

