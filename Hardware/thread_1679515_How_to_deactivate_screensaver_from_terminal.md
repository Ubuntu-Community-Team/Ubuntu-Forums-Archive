---
title: "How to deactivate screensaver from terminal"
date: 2011-02-01
forum: Hardware
---

### Post by Elwro on 2011-02-01
Hello,

I have an old Thinkpad on which I have installed Xubuntu 10.04. Unfortunately:

- the screensaver locks the machine so that even Alt-SysRQ-b does not work
- when I click on Applications -> Settings -> Screensaver, the system goes back to the login screen.

I would like simply to deactivate the screensaver. How is it done? In Ubuntu I'd use the gconf-editor, I think, but what about Xubuntu?

Best regards,

L.

---

### Post by Elwro on 2011-02-01
Heh,

```
sudo apt-get remove xscreensaver
```

seems to have done the trick.

---

