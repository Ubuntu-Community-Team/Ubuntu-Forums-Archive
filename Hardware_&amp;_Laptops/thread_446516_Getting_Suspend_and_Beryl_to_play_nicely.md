---
title: "Getting Suspend and Beryl to play nicely"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by Goombie on 2007-05-17
I'm having a problem with the suspend/resume function on my laptop (who doesn't?). 

I can suspend fine, but when I resume, I can use the desktop for about 10 or 20 seconds, then everything freezes. The mouse and keyboard don't respond, and I have to do Alt+SysRq+K. Even that doesn't work all the way, for when I log back on, it freezes up again. I use (would like to use) the suspend function on a regular basis, so this problem is kind of annoying for me. My system config is in my signature, and I'm also using Beryl for my window manager, with the open-source ATI drivers and AIGLX.
Thanks in advance!

---

### Post by meldroc on 2007-05-17
I have somewhat similar issues, only I'm running an Asus A8Js laptop, Core 2 Duo 2.0 GHz, 2GB RAM, Nvidia GeForce Go 7700 w/ 512MB for video, 120GB hard drive, running Feisty.

Methinks the video drivers don't save and restore their state correctly when doing OpenGL applications.  For me, if I use Beryl and suspend my laptop, it frequently will leave me with a black screen on resume, or otherwise crash or do flaky things.

Since both ATI/AMD and Nvidia have either proprietary drivers or sucky open source drivers, there's little to do but complain to them and ask them to fix their drivers.

I had a :shock: moment when I read through NVidia's Linux driver documentation and saw it mentioning that the drivers contained self modifying code...

---

