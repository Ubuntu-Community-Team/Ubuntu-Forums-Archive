---
title: "Mouse stuck in top right corner after reboot from Windows"
date: 2011-05-14
forum: Hardware
---

### Post by dacha on 2011-05-14
Hi

In an Xubuntu 11.04 Wubi install on a Packard Bell Dot S2, the touchpad works perfectly if I cold boot.

But if I reboot from Windows into Xubuntu, the mouse cursor is constantly pulled to the top right corner of the screen. Trying to move the touchpad causes it to nudge slightly, but it immediately flies back to that corner.

"xinput list" gives me:
Virtual core pointer
   Virtual core XTEST pointer
   PS/2 mouse
   AlpsPS/2 ALPS GlidePoint

"synclient -l" and "xinput list-props X" outputs are exactly the same on cold boot and reboot.

Any ideas?

---

### Post by Toz on 2011-05-14
Out of curiosity......

Does```
lsmod | grep psmouse
```
return a line with psmouse in it, like this?```
$ lsmod | grep psmouse
psmouse                59033  0 
```

If so, try the following:```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

---

### Post by dacha on 2011-05-16
Thank you. Yes, the psmouse module is loaded and reloading it fixes the mouse problem.

What does this mean?

---

### Post by Toz on 2011-05-16
Not sure, but I'm guessing that something is buggy with the psmouse module in your situation (rebooting from Windows). If you want to make this permanent (so you don't have to enter these commands every time), edit the file /etc/rc.local and put the commands before "exit 0" ala:```
modprobe -r psmouse
modprobe psmouse
exit 0
```
If that doesn't work, you'll have to throw something together to run when you login.

---

