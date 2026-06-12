---
title: "Error message in bootup (picture)"
date: 2008-07-21
forum: General Help
---

### Post by Kain000 on 2008-07-21
Hey everyone every time I boot up my server that I have to auto loggon I get the following message, witch causes me to click ok before it will boot up all the way.  Sufficed to say I do not want to have a mouse and monitor permanently attached to my server to boot it up.  any ideas?

Picture attached

---

### Post by confused57 on 2008-07-21
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

---

### Post by echo314 on 2008-07-21
Looks like you need to change permissions on the file. chmod or some similar command, followed by 664 and the file? do a quick search on changing file permissions, and you should be able to figure it out

---

### Post by damis648 on 2008-07-21
Try this in terminal:
```
chmod 644 $HOME
```
and then reboot.

---

