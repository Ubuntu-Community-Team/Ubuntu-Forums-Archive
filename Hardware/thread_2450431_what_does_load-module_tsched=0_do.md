---
title: "what does load-module tsched=0 do?"
date: 2020-09-13
forum: Hardware
---

### Post by yaminb on 2020-09-13
Hi,

What does tsched=0 do in load-module?

background:
I was experiencing some audio static that I was working around by just restarting pulse audio.
Recently, I googled a bit and found a fix that looks to have resolved it.

File: /etc/pulse/default.pa
from:load-module module-udev-detect
to:load-module module-udev-detect tsched=0

This does appear to fix it, but I can't seem to find out what it actually does? My quick googling says it's something to do with timer versus interrupt based scheduling. But is this bad to do? Will it degrade system performance?

---

### Post by yaminb on 2020-09-13
Did a little more research and came across this good link.

[http://0pointer.de/blog/projects/pulse-glitch-free.html](http://0pointer.de/blog/projects/pulse-glitch-free.html)

---

