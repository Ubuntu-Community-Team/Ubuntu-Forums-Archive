---
title: "Initramfs"
date: 2009-06-26
forum: Hardware
---

### Post by qemqemqem on 2009-06-26
An old Inspiron 8600, which has been running Jaunty fine for a couple weeks, has suddenly stopped booting and instead goes to BusyBox, which has an initramfs prompt.

How do I get out of this prompt?
How do I stop it from coming back?

I can't think of anything that might have sparked this, except that prior to this failure, I experienced trouble with the volume keys which ironically caused all sound to cease if they were pressed.  The computer rebooted fine twice with this problem.  I also installed KDE earlier.

I haven't found any commands that will get out of the prompt.  I haven't seen any other threads that match this situation.

Here are relevant error messages it gives me:

Starting up...
... IO APIC resources could be not be allocated.
...
kinit:trying to resume from /dev/disk/by-uuid/.38...
kinit:No resume image, doing normal boot...
mount:mounting /dev/disk/by-uuid/e93... on /root
failed: invalid argument
mount: moutning /dev on /root/dev failed: no such file or directory
mount: moutning /sys on /root/sys failed: no such file or directory
mount: moutning /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init
no init found. Try passing init= bootarg

Busybox v1.10.2 ...

---

### Post by Ayuthia on 2009-06-26
Have you tried to go back to the previous kernel?  When starting up, there should be a grub menu (if there isn't one, press escape).  There should be an option to go back to 2.6.28-11-generic.

It sounds like linux-headers or linux-image did not fully install on the update.

---

### Post by Quintijn on 2009-08-27
I get the same problem, also with an Inspiron 8600. Unfortunately loading 2.6.28-11-generic kernel does not work on my system. Same error persists.

Any other ideas? (My last kernel is 2.6.28-15-generic)

Thanks, Quintijn

---

### Post by Quintijn on 2009-09-02
My solution appeared to be: restart from the Install disk. After that action the missing files appeared to be restored again, and the system started right away.

Quintijn

---

