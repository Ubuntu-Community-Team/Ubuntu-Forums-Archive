---
title: "Shutdown problem in Ubuntu 10.04 on HP tx2500z"
date: 2010-04-04
forum: Hardware
---

### Post by kontiky on 2010-04-04
I've installed Ubuntu 10.04 beta1 on my HP tx2500z. The main problem for  now is Ubuntu doesn't power off my tablet pc during shutdown. Moreover,  pc doesn't react of any keyboard pressings and I must remove battery to  power off it. How can I fix this problem?
One linux guru told me about probably some problems with my sound or  video card drivers. How can I check this? Where can I see system logs  about shutdown process?

---

### Post by cak3 on 2010-04-26
Looks like you are having a similiar issue to what I was. I found a solution, if you still need it.

it is at [http://ubuntuforums.org/showthread.php?t=1463092](http://ubuntuforums.org/showthread.php?t=1463092)

the short fix is to put the .conf file in the second post in /etc/init. More details are in my first post and in the bug report I linked, if you are curious.

---

