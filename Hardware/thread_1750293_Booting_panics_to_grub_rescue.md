---
title: "Booting panics to grub rescue"
date: 2011-05-05
forum: Hardware
---

### Post by Pseudopipegraphic on 2011-05-05
Hello,

Yesterday my Ubuntu (10.10) Eee netbook, which had been working basically fine, stopped.  After closing the lid to do something and opening back up, the usual password prompt did not display, though the mouse cursor was stil visible and usable, on the black screen.  After trying to "wake it up" with the keyboard, I rebooted.

It got all the way up to the usual Grub prompt with OSs to choose from.  However, when I tried to boot, the system dropped to initramfs after displaying an error like this:

```
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg
```I tried launching the Ubuntu recovery mode, but that just printed the same error after more text.

I googled a bit and found the suggestion that my filesystem was corrupted, so I got a LiveUSB (no CD drive) and ran fsck /dev/sda1, but:

```
fsck from util-linux-ng 2.18
e2fsck 1.41.12 (17-May-2010)
Ubuntu: clean, 11/4685824 files, 340107/18734342 blocks
```

so I guess that's not the problem.  Furthermore, now when I try to boot from the hard drive, it doesn't even display the Grub selection but just drops to

```
error: no such partition
grub-rescue >
```

so I fear I may have made things worse.  Could I get help with this?

---

