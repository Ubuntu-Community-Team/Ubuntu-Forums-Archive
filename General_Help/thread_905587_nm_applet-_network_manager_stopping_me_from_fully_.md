---
title: "nm applet- network manager stopping me from fully shutting down"
date: 2008-08-30
forum: General Help
---

### Post by bigdee973 on 2008-08-30
hello im having a problem where my ubuntu machine wont fully boot at shutdown it tells me something about network manager make sure the message bus is running or something. when i press the power button it restarts the computer and then i have to immediately press the power button again to shut off as you can imagine this is not a safe way to power down a machine with expensive peripherals installed inside it such as the hard drive.  any clues to how to prevent this message from appearing and having a full shut-down?

---

### Post by damis648 on 2008-08-30
Try shutting down with terminal via:
```
sudo shutdown -h now
```

---

