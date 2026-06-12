---
title: "Starting X Programs At Boot With /etc/init.d/"
date: 2008-08-19
forum: General Help
---

### Post by EPEC on 2008-08-19
Hello,

I am trying to run a program, in WINE, which requires X11 to execute.  I would like it to start up with the system.  I tried the instructions on the Ubuntu wiki about how to make WINE programs start from boot, but they don't work.  I think they are written for a "desktop environment", whereas my server is a Ubuntu CLI that I happened to install Xfce on.  I connect to Xfce using VNC.

What I want it to do:
Effortlessly run this command at boot, such that the program starts.

wineconsole --backend=user cmd.exe /c "C:\Program Files\Path\To\Program.exe"

When I run that command line inside my X session via VNC, the program starts up.  How can I make this happen at boot time?

Thanks!

---

