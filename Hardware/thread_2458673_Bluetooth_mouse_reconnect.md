---
title: "Bluetooth mouse reconnect"
date: 2021-03-02
forum: Hardware
---

### Post by hornetster on 2021-03-02
Just wondering...
Have a multiboot PC, with several Linux derivatives (couple of ubuntus, opensuse, tumbleweed) and a Win10, and am trying to use a bluetooth mouse across all systems.
Is it  possible to set them up to reconnect from one boot, in one OS, to a reboot into another OS?
Have found that 'generally', if I boot into one, then reboot into the same again, the mouse connects OK, but when I move from 1 OS to another, I can't even "reconnect", having to delete the original mouse config, and pair again...
Is there any way to fix this? I suspect not...
Thanks.

---

### Post by CelticWarrior on 2021-03-02
Your suspicion is the same as mine.
I think it has to do with how Bluetooth HID works. Unlike Bluetooth audio devices that typically can be connected to a few alternating sources without the need to re-pair them, mice and keyboard support one connection only.

---

