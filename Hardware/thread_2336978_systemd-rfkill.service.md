---
title: "systemd-rfkill.service"
date: 2016-09-13
forum: Hardware
---

### Post by phileconte on 2016-09-13
Hi,

I've got a serious problem : 
- my laptop friezed, the keyboard and the mouse don't reacted and I was forced to shutdown the power because I was unable to access a TTY with alt-ctrl-F1
- on start-up, grub passed, session began but was blocked
- in recovery mode, same thing
- in recovery, verbose mode, 
...[OK] started Load/Save RF Kill switch status
 systemd-rfkill.service and then, nothing append, the laptop is blocked
- I'm unable to use a live CD (Kubuntu 16.04 blocked, boot-repair says kernel panic...)

I don't know what to do because even a re-installation seems impossible. Is it possible to modify the grub to avoid rfkill ?

Thanks for your ideas

---

### Post by phileconte on 2016-09-13
I got the solution by myself using Internet search: 
- I cleaned the Kubuntu live CD and the optical probe of the floppy disk and was able to have a live session
- I have renamed the systemd.rfkill file to .old
- reboot, all is fine !

Sorry to post my message too early.

---

