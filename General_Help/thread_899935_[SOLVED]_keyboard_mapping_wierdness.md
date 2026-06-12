---
title: "[SOLVED] keyboard mapping wierdness"
date: 2008-08-24
forum: General Help
---

### Post by csogilvie on 2008-08-24
I recently built up an Ubuntu 8.04 desktop machine in my attempts to deal with the fact that I now have to manage a 8.04 server for work.

Anyway, the server is now working like it should, but my hope PC is not strangely enough, and I think I did exactly the same thing on each machine.

The problem, VNC to session:1 (the one I'd log into using SSH for remote access) seems to mis-map my keyboard.

The following phrase "This is not a drill"
Gets mapped to "1Nklb7lb7\zn7a7fvl'"

If I VNC from inside my local network to the console session :0, everything works just fine.

Strangely enough, I made the same configuration  changes to the server, and my keyboard works exactly as I expected.

They are not identical hardware, but the same changes were made to each system.

If anybody could suggest anything, or needs me to generate some output of my system setup, for further analysis, I'd greatly appreciate it!

If you do need some output, please tell me how to get it, as I'm on the painful part of the linux learning curve.

Thanks for your time!

---

### Post by mssever on 2008-08-24
Have you verified that you're using the correct keyboard layout?

---

### Post by csogilvie on 2008-08-24
No worries folks!  After a few more google searches I found the solution!

This problem was already well discussed on other forums.

The fix was to add the following line in my "xstartup" in my .vnc folder, just before the "exec gnome-session &"

"export XKL_XMODMAP_DISABLE=1"

This fixed my issue!

Thanks for your time...  And I hope re-documenting this here might help somebody else.

---

