---
title: "Open the CD-tray by terminal command?"
date: 2008-05-28
forum: Hardware
---

### Post by yc2 on 2008-05-28
Hi,

I use this excellent recovery CD: [http://www.sysresccd.org/](http://www.sysresccd.org/). However, neither when using it nor shutting it down ("shutdown -h now"), is it possible to open the tray by pushing the button on the tray. (HP Pavillion 6751.eo) What I do is to go into BIOS at next upstart and remove the CD.

Please tell me, is there a way of opening the CD-tray from this recovery environment (mostly terminal based). (Preferably a way not including a bent paper-clip ;))

Thanks

---

### Post by nick_h on 2008-05-28
Have you tried the *eject* command?

For the manual page type:
```
man eject
```

---

### Post by yc2 on 2008-05-28
Thank you nick_h! Worked perfectly. (I just didn't know of the command :redface:)

---

