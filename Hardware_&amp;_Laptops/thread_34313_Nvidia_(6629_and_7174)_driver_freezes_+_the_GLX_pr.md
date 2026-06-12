---
title: "Nvidia (6629 and 7174) driver freezes + the GLX problem (segfaults)"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by Cybolic on 2005-05-14
After upgrading to Hoary I've been experiencing the following two problems:

[list=1]
[*]When using the Hoary-supplied 7174 nvidia driver, X freezes after only a couple of seconds, so I've gone back to using version 6629, which seems mostly stable.
But every once in a while, X freezes (except the mouse, oddly enough). I usually escape the freeze by typing Ctrl+SysRq+I to kill all processes.
[*]The other problem I'm having after upgrading, is that MPlayer, Wine, glxgears and anything else that has anything to do with GLX, segfaults on running. This only happens after a couple of log ins.
[/list]

After experiencing one of these two problems, the only way it seems to get my system running again is to recompile and reinstall the nvidia module from source (the nvidia-installer).

This last thing is what really puzzles me - shouldn't simply reinstalling it fix the problem? Why is a recompile necessary?


I seem to remember reading somewhere that the problem is caused by the switch from XFree86 to X.org and that the problems dissappear if downgrading the X-server, but since I don't have a local copy of an older version, and can't seem to find one online, I can't test if this is true.

Any suggestions as to why this is happening is very welcome.

Cheers,
*Cybolic*


P.S. I see that this is the same problem as described at [http://www.ubuntuforums.org/showthread.php?t=32298&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=32298&highlight=nvidia) *EDIT: Except that this occurs with both the 6629 and the 7174 driver for me*.

---

### Post by fsman on 2005-05-14
I think I am having the same problem. See my post today Nvidia / opengl crash

---

