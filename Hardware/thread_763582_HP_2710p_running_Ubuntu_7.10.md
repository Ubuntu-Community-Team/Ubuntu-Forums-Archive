---
title: "HP 2710p running Ubuntu 7.10"
date: 2008-04-23
forum: Hardware
---

### Post by daimyo83 on 2008-04-23
Dear all

I would appreciate any help with some hardware/software issues I'm having with running Gutsy on a HP 2710p.

- My HP PL800A tablet pen is not recognized and I'm having a really hard time locating any support, I've scoured a lot of forums but they all talk about Wacom tools. But as far as I know my Tablet pen isn't supported by Wacom? I really want to use the pen, because it rocks and because the little built in mouse sucks :-P

- I can't get Sleep/Suspend to function. When closing the display the screen shuts, but the PC does not go into sleep/suspend mode.

Thanks for any help.  
Oh, and BTW, I'm completely new to Linux, this is only my second unit I'm running Ubuntu on, my first was a Mac G3 a year or two a go.

Thanks

---

### Post by francisco_athens on 2008-06-27
2710p works well in Hardy. Similar issues, but they can be resolved.  I've started a wiki page here:
[https://wiki.ubuntu.com/LaptopTestingTeam/HP2710p_Hardy](https://wiki.ubuntu.com/LaptopTestingTeam/HP2710p_Hardy)

your lid closing is likely hanging the kernel and appears to be a problem with certain HP notebooks, according to bug #157691 here:
[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/157691](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/157691)
for me adding the following before "exit 0" in my /etc/rc.local works fine:
```
echo "1" > /proc/acpi/video/C09A/DOS
```
but there are perhaps better ways to fix this in the bug report..

best of luck!

---

