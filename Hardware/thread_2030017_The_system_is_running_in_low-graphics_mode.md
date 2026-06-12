---
title: "The system is running in low-graphics mode"
date: 2012-07-20
forum: Hardware
---

### Post by Futurama on 2012-07-20
Hello,
 
When I startup my laptop (Packard Bell EasyNote MX52 with Ubuntu 12.04) I get the message 'The system is running in low-graphics mode'. My cursor doesn't work and I also can't get in the terminal because when I press Crtl + Alt + F1 I get a black screen.
How can I solve this problem?

---

### Post by N0oki3 on 2012-07-21
hello there. This standard trick might help you. Inside of tty1

```

sudo rm /etc/X11/xorg.conf
sudo startx

```

---

### Post by Futurama on 2012-07-21
I can't get in tty, when I press Ctrl + Alt + F1 or Esc I get a black screen with flashing white lines.

---

