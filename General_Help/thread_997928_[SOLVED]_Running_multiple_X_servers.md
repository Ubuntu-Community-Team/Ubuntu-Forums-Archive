---
title: "[SOLVED] Running multiple X servers"
date: 2008-11-30
forum: General Help
---

### Post by siddartha on 2008-11-30
Is it possible to run multiple X servers on the same machine with only one display? I have seen that you can do that with a VNC server quite easy, but that doesn't use the same display. I am looking to something closer to the old multiple consoles, probably with different configurations.

---

### Post by siddartha on 2008-11-30
The default gdm/kdm located the display as :0 (the first). So in console all you have to do is ```
startx -- :1
``` where :1 can be any number and that would be the refference for that particular display.

---

