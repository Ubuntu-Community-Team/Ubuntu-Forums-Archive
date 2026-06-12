---
title: "[SOLVED] Strange boot"
date: 2008-09-29
forum: General Help
---

### Post by gary0 on 2008-09-29
Hi all,
here's a strange one...

Last night my computer failed to shutdown (or at least was taking a long time), so  I did alt-ctrl-backspace and shut it down from there. This morning when I booted it said:
Grub loading stage 1.5Read error (no space in there)

So I rebooted and got:
Grub error 15

So I rebooted again and got:
Grub error 18

So I rebooted and got:
Bash>

I typed boot at the prompt and got:
Kernel must be loaded
Bash>

I typed Kernel and got:
Error

So I rebooted again and it started properly!

Anyone know what happened and why it did this? Is it like windows where if you boot and shutdown 3 times in safe mode, it fixes boot problems? Did it repair itself?

Any insight into this would be helpful.

Regards,
Gary.

---

### Post by Herman on 2008-09-29
My guess is your file system was probably scrambled up a little. It is GRUB stage1_5's job to try to understand file systems and find stage2 inside the file system somewhere and hand over control it it.
Then stage2 takes over and does the booting.
Some error messages come from stage1 in the MBR, other error messages come from stage1_5, or from stage2.
Refer to: [14 Error messages reported by GRUB]("http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting") - the Gnu/GRUB Manual.

I don't know why you got a series of different Error messages, I don't think Ubuntu can fix itself, you were just lucky. Maybe it wasn't too corrupted. It looks like it got a little further each time until it finally booted.
Normally you would have needed to run a file system check before booting.

Ubuntu does run a file system check during boot up but you can run a better one yourself from a Live CD.
A good one for an ext3 file system is,
```
sudo e2fsck -C0 -f -v -p /dev/sda2
```Where: the file system you want checked is '/dev/sda2', replace that with some other partition number as required.
NOTE: Never run a file system check on a mounted file system.

---

### Post by gary0 on 2008-09-30
Thanks Herman. I will do that.

Gary

---

