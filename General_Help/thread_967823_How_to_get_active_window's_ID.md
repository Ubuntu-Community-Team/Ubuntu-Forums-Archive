---
title: "How to get active window's ID?"
date: 2008-11-02
forum: General Help
---

### Post by crazyfuturamanoob on 2008-11-02
Hi! I want to get currently active window's ID.

When the window is minimized, it's ID and name changes, and when I expand it again, it's name and ID changes.
And when it is active, capture of mouse is impossible to all other programs.

So using xwininfo isn't the way, because it needs to capture mouse.

I made a simple python script that waits 5 seconds. And during that five seconds, I expand the window, and it is now active.

I'd just want to get it's ID when it is active, how to do that?
For example, "python wait.py && getactivewindowinfo".

And the window/program is Urban Terror.

---

