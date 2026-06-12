---
title: "[SOLVED] deactivate graphics driver from terminal"
date: 2008-11-01
forum: General Help
---

### Post by jakupl on 2008-11-01
I just upgraded to 8.10 but when I had done that, the screen was black.
I just figured - what the heck, i might as well just do a clean install - and so I did.

It worked beautifully until i activated my proprietary graphics driver "ATI" and when I rebooted, it was black again. AHA! that's the problem!

so now my question is: how do I deactivate it from the terminal, in have dropped to root shell prompt, but don't know what to do here.

thanks in advance

---

### Post by taurus on 2008-11-01
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jakupl on 2008-11-01
> **taurus said:**
> ```
dpkg-reconfigure -phigh xserver-xorg
```

Yes of course. That did it. Thank you very much

---

