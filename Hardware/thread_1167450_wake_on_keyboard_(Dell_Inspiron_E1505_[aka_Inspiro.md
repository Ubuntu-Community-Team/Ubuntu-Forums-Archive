---
title: "wake on keyboard (Dell Inspiron E1505 [aka Inspiron 6400])"
date: 2009-05-22
forum: Hardware
---

### Post by peppergrower on 2009-05-22
I'm running Ubuntu 8.10 on my laptop, which has a faulty lid switch.  This means it will wake from sleep (S3) randomly while in my bag.  This is obviously a bad thing, and the only real solution I came up with is to disable the lid switch and enable something else.

I discovered /proc/acpi/wakeup, and figured I'd just disable the lid switch (LID) while leaving the power button (PBTN) enabled (echo LID > /proc/acpi/wakeup).  Unfortunately, the two are tied together somehow, and if I disable one both end up disabled.

So now I need to either (a) find a way to separate the two, or (b) enable something else to wake my laptop.  From what I've found the first would be pretty complicated (involving editing my DSDT), while (b) seems like it should be pretty simple.  I picked the keyboard and/or touchpad as the most obvious options.

Only...I tried enabling everything in /proc/acpi/wakeup (and verified that they were enabled), and after suspending to RAM the keyboard and touchpad still wouldn't do anything.

Someone else in [another thread here]("http://ubuntuforums.org/showpost.php?p=6902687&postcount=32") mentioned that you should use /sys/devices/ instead, but I haven't been able to figure out where my "keyboard" device is to enable it there.  Per someone else's suggestion there, I checked my BIOS options, and there's nothing there about enabling wake on keyboard.

Does anyone have any other ideas for enabling a "wake on keyboard" from standby (S3)?  Or a simple way to detangle the LID and PTBN entries in /proc/acpi/wakeup so I can disable just one of them?

---

