---
title: "ubuntu fails to start simple graphics mode"
date: 2008-11-02
forum: General Help
---

### Post by link0007 on 2008-11-02
Hi, I recently updated from 8.04 to 8.10,  but during the upgrade some error messages were thrown at my head, and the upgrade was aborted. But now when I boot ubuntu, I get a message that it needs to be started in simple graphics mode. Problem is that ubuntu hangs itself at that message. So I can't press ok, nor move the mouse.

How can I fix this?

---

### Post by taurus on 2008-11-02
When you turn on your machine, you would see a GRUB menu.  If you don't see it, press ESC (you have about three seconds to do that) at the GRUB screen to bring up the menu.  In there, you would see a recovery mode option.  That's what you want to highlight (using the arrows) and boot.

---

### Post by link0007 on 2008-11-02
Ehm, I did both the "fix defect packages" (or something like it) and the "fix x-server", but both failed to fix it.

Is it possible to reinstall the nvidia driver?

---

### Post by link0007 on 2008-11-03
bump?

---

### Post by link0007 on 2008-11-04
I tried the command
```

dkpg-reconfigure xserver-xorg

```
today (in root shell of recovery mode), and it didn't work because pretty much all packages are f*cked up (noticed that earlier when I let dpkg try to repair the broken packages). A chain of dependancy problems probably causes dpkg not to function. 

So is there a way to rebuild all packages from the ground up? Or just delete all packages and go back to default?

---

