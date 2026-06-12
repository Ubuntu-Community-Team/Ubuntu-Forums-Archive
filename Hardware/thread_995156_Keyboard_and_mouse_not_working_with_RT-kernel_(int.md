---
title: "Keyboard and mouse not working with RT-kernel (intrepid)"
date: 2008-11-27
forum: Hardware
---

### Post by mikkelbue on 2008-11-27
Hello guys

I have a problem with my macbook2.1 and intrepid ibex (almost fresh install, running realtime kernel 2.6.27.3). When I boot with the generic kernel, there is no problem, and everything works as it should, but when I boot with the realtime kernel, X records 2 events each time I press a button on my keyboard once (if I press "j", it writes "jj"), and the mouse is so unresponsive, it is unusable. I cannot log in through gdm. I can shut down X (ctrl+alt+backspace), but I have the same problem in the terminal.

I can't really give you any terminal output (because I can't write any maningful commands), and I don't expect it is a problem with my xorg.conf, as the realtime kernel should be using the same settings as the generic one, which is working. If you need any specific output for diagnosis, please ask me for it, and I will see what I can do.

Please help. I cannot find any records of the same problem.

/Mikkel

---

