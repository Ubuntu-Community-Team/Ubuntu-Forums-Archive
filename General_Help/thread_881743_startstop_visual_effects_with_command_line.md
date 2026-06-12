---
title: "start/stop visual effects with command line"
date: 2008-08-06
forum: General Help
---

### Post by Creat on 2008-08-06
Hey

I've been looking around for a while but obviously I'm not looking at the right place. Can anybody please tell me what the commands are to start visual effects with the "normal" options and the one to stop the visual effects (or option "none")?

Indeed, I have a dual screen set up that I start using a launcher in the panel (it calls a command like "xrandr --output VGA --mode 1280x1024 --right-of LVDS") and I have the something similar to turn the dual mode off. However, it seems that my video card is not powerful enough to support visual effects with dual screen enabled. So, I wanted to add the commands to turn on and off the visual effects at the same time that my dual screen mode. Unless someone has an idea for enabling my visual effects with the dual screen mode.

Thanks,
François

---

### Post by sayakb on 2008-08-06
To turn off:
```
metacity --replace
```
To turn on:
```
compiz --replace
```

---

