---
title: "FGLRX graphics driver post-release updates won't install"
date: 2012-06-28
forum: Hardware
---

### Post by andizam on 2012-06-28
I'm a bit of an Ubuntu newbie. I just installed Ubuntu 12.04 on my Dell Inspiron 15R (M5010) and the graphics either doesn't load normal Ubuntu, or simply takes ages to load the desktop (ridiculous amount of time like 45 minutes to load an unresponsive desktop) so I choose to log into Ubuntu 2D. I install all proprietary drivers including normal FGLRX graphics, but that doesn't solve the problem. Now I get an error installing the post-release updates. It tells me to check /var/log/jockey.log but I've no idea what that log is saying. Any help please?

---

### Post by broken pixel on 2012-08-06
I just installed Mint 13, I did the apt-get install fglrx ect, etc and used the commands to add hardware exeleration. I tried installing the post release update and got the same error. I do have with apt-get the version below installed.

8.96.7-120312a-135598C-ATI
8.96.4 
2.14
1.3
OpenGL 
4.2.11627

---

### Post by Mark Phelps on 2012-08-09
Sorry, but in general, the post-release drive installs do NOT work.

If the "problem" is the enormous delay in getting to a working desktop (you said 45 minutes!), video drivers are not going to be the cause of that.

It's more likely a failing hard drive -- with bad sectors that are forcing massive numbers of re-reads.

---

