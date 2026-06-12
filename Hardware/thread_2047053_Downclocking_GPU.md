---
title: "Downclocking GPU"
date: 2012-08-24
forum: Hardware
---

### Post by p0o9I on 2012-08-24
Hello,
I would like to run my PC with multiple displays. But it seems that nVidia is not able to downclock the card it this mode.
However, as I first installed Kubuntu (I had almost no idea what was happening suring the installation) tthe system loaded not nVidia drivers but Nouveau. Well, today aftr reinstallation I have certified nVidia drivers. Im quite happy that now I can know something about the temperature etc. Well while the Nouveau drivers cant tell anything about state of my graphics, they can do an awesome thing ->Downclock the GPU while running on multiple displays.
Is there some possibility to change the GPU PowerMode (as in PowerMizer) manually? I need to force it to 0 for Iddle, 1 for Video and 3 for games as it was designed.. 
Thank you very much

---

### Post by beboylips on 2012-08-25
As far as I know it scales automatically to meet performance requirements. Forcing it to run at lower frequencies would impact performance significantly.

---

### Post by p0o9I on 2012-08-25
Actually the performance is good at the low levels.. Im forcing it with succes on windows. mode 0 for GUI mode 1 for video and mode 2 for games. The GPU itself should take it to the low level even with two displays, but theres a known bug in nVidia design that somehow disables this automatization. (They claim it is in "design" but obviously its somewhere else as we can override it with such a simple thing like nVidiaInspector, which regardly is not for Linux..)

---

