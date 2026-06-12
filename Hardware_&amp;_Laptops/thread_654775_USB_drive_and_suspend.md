---
title: "USB drive and suspend"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by Greg T. on 2007-12-31
I was having a couple problems recently that turned out to be related. The first was a mysterious, blank warning box that would pop up occasionally when I'd come out of suspend. The second was a sporadic failure of the PC to go into suspend at all.

The problems were due to the fact that my two USB drive(s) were not being unmounted before entering suspend. One device is a Lexar thumb drive that I use occasionally; the other is a Maxtor OneTouch external hard drive that I have used infrequently. The mounted thumb drive triggered the pop-up message, which I eventually realized was an "unsafe device removal" message. The Maxtor drive prohibited the PC from suspending as long as it was mounted. 

The solution (more of a workaround, really) to both problems was to add "umount /media/[NAME OF DRIVE]" commands to /etc/acpi/prepare.sh. Credit goes to a post in this discussion: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/92091](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/92091). In my case, that meant adding the following:

```
umount /media/BACKUP
umount /media/LEXAR
sleep 2
```

The "sleep 2" command was needed to ensure that the unmounting was completed before the PC goes to sleep. 

Ideally, this would all be handled automatically without manual edits to the suspend script, but this approach took care of the issue for me.

---

### Post by K.Mandla on 2007-12-31
Moved to Hardware and Laptops. :)

---

