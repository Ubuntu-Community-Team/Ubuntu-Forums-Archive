---
title: "Geforce2go with latest nvidia drivers"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by marcozs on 2006-11-11
Hi everyone!

I installed Edgy on my old Inspiron 8000. I tried to install the latest nvidia drivers from the amaranth repo and everything worked out fine or it seems so (see the attached image). But there's something wrong: I wanted to test mplayer with gl selecting the proper driver in the video options (tried both gl and gl2) and I can't put the video fullscreen. When I try any application using gl in fullscreen either it won't work properly (mplayer, screensaver) or it restarts my xserver (zsnes, Warcraft III with wine).

I even tried beryl with aiglx, it recognizes the new nvidia drivers but it keeps loading for a long time and then it just hangs when the windows decoration are loaded. I think the software isn't really using the hardware accelleration... is there a way I can check it? Any ideas of how to solve it?

Thanks
Marco

---

### Post by marcozs on 2006-11-11
Toc toc ...

---

### Post by dragonfyre13 on 2006-12-01
[http://www.ubuntuforums.org/showthread.php?t=297689&highlight=fullscreen+nvidia](http://www.ubuntuforums.org/showthread.php?t=297689&highlight=fullscreen+nvidia)

It's a bug with the latest stable drivers from Nvidia. Grab the latest (97xx) drivers from the nvidia site (they are beta) and it fixes it, or you can downgrade to the 8xxx version which doesn't have the bug. Alternatively, downgrading to 9625 works great for me, and it gives me the special functionality to run beryl I still need. Ick, it's annoying, but the 97xx drivers are shweet. Check out the tutorial on installing them here though. They aren't a simple procedure.

HOWTO: [http://www.ubuntuforums.org/showthread.php?t=296933&highlight=nvidia+9742](http://www.ubuntuforums.org/showthread.php?t=296933&highlight=nvidia+9742)

---

