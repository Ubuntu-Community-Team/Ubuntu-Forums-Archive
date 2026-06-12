---
title: "I have to troubleshoot xorg..."
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by Chareos on 2005-10-16
Hi there,

as title explains, I'm having problems with nvidia+xorg. To troubleshoot it I need to boot-in in text mode. I was guessing... is there a way / parameter to pass lilo to boot to graphic or to text, decidingthis at boot time ?

thanks

---

### Post by cbudden on 2005-10-16
Why not just boot normally, edit it and restart X?

---

### Post by Chareos on 2005-10-16
Because it boots regularly, then tries to start xorg and BUM - black screen, no way to kill the server or change virtual terminal. Can only power off.



Long story explained:

Due to the *bizzarre* procedure I should follow to get lirc working it the ubuntu way, I prefer to compile my own kernel. This requires also nvidia drivers to be installed manually. All fine (I removed nvidia-glx with apt-get), if I startx everything works. BUT, after I reboot, I get the black screen with system freeze.

Note: I've kept the ubuntu kernel, just in case. From there I can look at var/log/Xorg.0.log.old and see what happens...
File content is just a line of @@@@@@@@@@@@@@@@@@@@@@@@@

I've to understand what happens, but booting between 2 kernels is somewhat not convenient (I cannot reinstall nvidia drivers from the ubuntu kernel for example).

---

