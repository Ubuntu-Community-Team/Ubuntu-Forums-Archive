---
title: "Installing on Dell Vostro 200"
date: 2009-01-11
forum: Hardware
---

### Post by paulehoffman on 2009-01-11
I could not install 8.04 on a Dell Vostro 200 desktop: I would always drop to BusyBox. Fortunately, the answer was over on <http://ubuntuforums.org/showthread.php?t=564582> response #5:

In the initial choices, select "Install" but press F6 and add "irqpoll" to the end of the kernel options. 

That pointer says you also need to ad "irqpoll" to the end of the grub boot options, but I found that it had already been added.

---

