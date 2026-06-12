---
title: "[SOLVED] ubuntu won't shutdown"
date: 2008-07-17
forum: Hardware
---

### Post by villageillness on 2008-07-17
Alright i kinda have this weird problem and wondered if there was a fix for it.

The problem is ubuntu wont shutdown when i decided to shutdown the system. I did some searching and found a thread where some people are having the same problem.

[http://ubuntuforums.org/showthread.php?t=603054](http://ubuntuforums.org/showthread.php?t=603054)

IN the above thread, a few people offered some fixes. One was adding the parameter acpi=force to the grub menu.lst.

Once i did that, ubuntu seemed to shutdown perfectly fine and everything is ok. However, now when i boot ubuntu from hd it hangs during loading process.

Then i remembered that i need the parameter "acpi=force" to be set to "acpi=off" in order for it to boot up normally.

So i get back into ubuntu, and edit the grub menu.lst file back to "acpi=off" and yes it loads up normally again. But now it does not shutdown.

So i tried adding "acpi=off" and "acpi=force" on the same line, to see if it would shutdown...and yep it did shutdown, but now it doesn't boot up.

So is there any idea of what i could try?

Thanks.

---

### Post by villageillness on 2008-07-17
Not to worry guys, it seems to be working now :)..don't know if that's a good thing or bad thing lol.

We'll see how it goes.

---

