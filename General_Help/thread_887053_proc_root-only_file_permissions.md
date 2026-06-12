---
title: "/proc root-only file permissions"
date: 2008-08-11
forum: General Help
---

### Post by squaregoldfish on 2008-08-11
Some of the files in the /proc subsystem are changeable, but only by the root user (not even sudo) can edit them.

For example, I can change the brightness of my laptop screen by updating the file:

/proc/acpi/video/VID/LCD/brightness

but I can only do it as the root user.

Is there any way I can change the permissions so that any user can change this file?

TIA,
Steve.

---

### Post by cariboo on 2008-08-11
You could use in a terminal:

```
sudo -i
```

This will drop you into /root so will have to navigate back to /proc/acpi/video/VID/LCD/brightness and use your favourite command line editor.

Jim

---

### Post by squaregoldfish on 2008-08-18
Never knew about the sudo -i thing - thanks!

As it turned out, I got lazy and now run a chmod a+w in rc.local. Then anyone can change the brightness :)

---

