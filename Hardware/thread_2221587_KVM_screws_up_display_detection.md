---
title: "KVM screws up display detection"
date: 2014-05-02
forum: Hardware
---

### Post by this-is-spam-mail on 2014-05-02
I have several ubuntu machines hooked up to 1 KVM switch (DVI + USB). They all have fresh, fully updated installs of 12.04 ubuntu-desktop. Whenever I boot one with the KVM set to that display it hangs on boot with a message "stopping userspace splash", CTRL+ALT+F(?) doesn't give me a tty and I have to ALT+SYSRQ+K to get a tty. However, if I boot the machine with a different machine selected on the KVM all is fine.

I'm thinking that the KVM (8 port IOGear DVI KVMP) is messing with the display autodetection and messing with the boot process.

Any way to fix this or debug it? I'm thinking that if I can just tell the computer to always use a certain resolution than it should be ok. However, I don't know how to do this or if it will help.

Thanks in advance!

---

