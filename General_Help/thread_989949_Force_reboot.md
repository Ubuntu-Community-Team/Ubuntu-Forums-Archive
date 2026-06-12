---
title: "Force reboot?"
date: 2008-11-22
forum: General Help
---

### Post by SvenG on 2008-11-22
I've got two servers running Ubuntu 8.10. They've got some processes stuck in state D which can't be killed by any means (kill -9 does nothing). They are apparently also preventing shutdown. I tried shutdown -r now but nothing is happening.

Is there any way I can force a reboot? I won't be able to physically access these servers until Tuesday, so I can't cycle the power. I just want to tell it to reboot immediately, forget about waiting for stuff to shutdown properly.

---

### Post by PmDematagoda on 2008-11-22
Try using the magic SysRq keys by first pressing Alt+PrntScrn and while holding those two, press R+S+E+I+U+B in that order one after the other, that should reboot the PC.

---

### Post by SvenG on 2008-11-22
As I said I don't have physical access to the server until Tuesday. I need an option that works over SSH.

---

### Post by PmDematagoda on 2008-11-22
> **SvenG said:**
> As I said I don't have physical access to the server until Tuesday. I need an option that works over SSH.

Don't you have a keyboard? Or doesn't it work over SSH?

---

### Post by SvenG on 2008-11-22
Your suggestion doesn't work over SSH.

---

### Post by SvenG on 2008-11-22
I managed to do it by running the following commands from a su shell (*not* using sudo):

echo 1 > /proc/sys/kernel/sysrq
echo b > /proc/sysrq-trigger

---

### Post by merekat on 2008-12-08
When using RSEIUB, how do I get the SysRq function instead of PrintScreen? I have been having random crashes and am testing out RSEIUB, but print screen always comes up as soon as I hit Alt+SysRq/PrintScreen.

> **PmDematagoda said:**
> Try using the magic SysRq keys by first pressing Alt+PrntScrn and while holding those two, press R+S+E+I+U+B in that order one after the other, that should reboot the PC.

---

