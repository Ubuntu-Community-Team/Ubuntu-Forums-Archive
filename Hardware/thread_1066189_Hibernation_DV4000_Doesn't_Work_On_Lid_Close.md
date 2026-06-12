---
title: "Hibernation DV4000 Doesn't Work On Lid Close"
date: 2009-02-10
forum: Hardware
---

### Post by yochaigal on 2009-02-10
Hello all.  I've been researching this problem for about a year now.
Hibernation used to work fine in Gutsy, but in intrepid it stopped functioning correctly.  I can hibernate by going to system > shutdown > hibernate, but when I close the lid nothing happens. I believe it's a GNOME issue (possibly video-card related?) as I can hibernate on lid close while in tty (ctrl+alt+f1).  I can also force it to hibernate on lid close by running this command:

sleep 15 && cat /proc/acpi/button/lid/*/state

This causes the laptop to wait 15 seconds before checking th state of the lid (open or closed).  If I shut the lid immediately after entering the command it hibernates!!! It also prints "state: closed" so I assume it's working correctly there as well.

So what now? Any ideas?

---

### Post by yochaigal on 2009-02-14
It's now hibernating automatically, but only after 10-15 seconds after closing does it hibernate.  Any way to decrease the wait time?

thanks

---

