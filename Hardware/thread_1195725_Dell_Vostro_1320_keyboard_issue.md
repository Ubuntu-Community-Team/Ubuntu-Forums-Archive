---
title: "Dell Vostro 1320 keyboard issue"
date: 2009-06-24
forum: Hardware
---

### Post by taslinux on 2009-06-24
Other people have noticed this: the keyboard and touchpad don't work after booting to the login screen. So far (20 boots?) I've found that both work again after restarting from the login screen. To do the restart from the GUI, you need an external mouse or keyboard.

Not clear what's happening here. Comparing the boot logs between the first, failed boot and the second, successful boot, the only difference I can see is the line

input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5

in the successful boot log.

Where does the command to set up this input come from during the boot, and how to fix it so the keyboard and touchpad always work?

P.S. I run 9.04, ignore the profile details, and the problem existed before the latest hal update (i.e., in ...ubuntu 1)

---

### Post by patrick82 on 2009-07-04
I have solved the problem on my Vostro 1320 in
/boot/grub/menu.lst

add
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
to the kernel line.

kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=91013859-dfec-4a84-ae8d-21233f16c89a ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop

:guitar:

---

### Post by taslinux on 2009-07-05
Many thanks, that seems to have fixed it! It's been an annoying problem because it's intermittent: some days the keyboard and touchpad worked on a cold boot, sometimes not.

Can you explain what the kernel line addition is doing?

---

### Post by bobsta101 on 2009-07-25
Hey
I have no idea what the kernel line is doing. but the bug is logged here...

[https://bugs.launchpad.net/ubuntu/+bug/334249](https://bugs.launchpad.net/ubuntu/+bug/334249)

and that has the workaround posted by a user.

---

