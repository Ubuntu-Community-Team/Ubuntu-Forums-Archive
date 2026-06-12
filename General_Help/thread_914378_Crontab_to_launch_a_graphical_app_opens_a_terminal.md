---
title: "Crontab to launch a graphical app opens a terminal window"
date: 2008-09-08
forum: General Help
---

### Post by Harri2097 on 2008-09-08
I'm pretty new to Linux in general, and having just discovered the joys of symlinks I'm playing around with crontabs at the moment. I've scoured Google and Ubuntu Forums but I've not been able to find the answer to an annoyance I've come across.

Basically I'm creating a crontab (using Gnome Schedule 2.0.2) to launch uTorrent with Wine at 9pm and then kill it again at 10am to get around my ISP's annoying throttling policy. It seems to work OK, except that every time they run, they open up a terminal window. 

Can anybody advise me how to get the task to run without generating a terminal window? Commands below:

```
0 10 * * * killall uTorrent.exe >/dev/null 2>&1 #JOB_ID_3
0 21 * * * wine "/home/harri/.wine/drive_c/Program Files/uTorrent/uTorrent.exe" >/dev/null 2>&1 #JOB_ID_4
```

Any help would be greatly appreciated!

---

