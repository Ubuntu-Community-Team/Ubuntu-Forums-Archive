---
title: "Suspend broke my display"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by ooglyboo on 2008-01-03
Hi everyone.

I just installed Ubuntu 7.10 on New Year's and everything has been working well up until now. Last night I clicked on the quit symbol and chose "Suspend" and the monitor and the computer shut off. The same thing had happened to me when I had used "Hibernate" earlier that day, but when I pressed the power button on my computer after hibernating it went back on without any problems. But now, after suspend, when I turn on my computer my display doesn't work. It just says "NO VIDEO INPUT" and the computer's lights flash. I don't think the problem is with my monitor because I disconnected it to test it on another computer after this and it worked. If it helps, my computer's a desktop PC and I'm using the Intel x86 version of Ubuntu Gutsy. I didn't install any software (my computer was never hooked up to the Internet) or modify any configuration files since my install a few days ago.

Can anyone suggest what I could do to get my monitor display working again? Thanks in advance.

---

### Post by sonofusion82 on 2008-01-03
if you have an nvidia graphics card, perhaps you can have a look at this thread [http://ubuntuforums.org/showthread.php?p=4060981](http://ubuntuforums.org/showthread.php?p=4060981) on modifying /etc/default/acpi-support

i also have similar symptoms with suspend/hibernate in my recent gutsy installation.

---

### Post by ooglyboo on 2008-01-04
> **sonofusion82 said:**
> if you have an nvidia graphics card, perhaps you can have a look at this thread [http://ubuntuforums.org/showthread.php?p=4060981](http://ubuntuforums.org/showthread.php?p=4060981) on modifying /etc/default/acpi-support

i also have similar symptoms with suspend/hibernate in my recent gutsy installation.

I don't know what my video card is. But I can't modify any files because I can't get my monitor to display anything. I tried putting in the Ubuntu Live CD to re-install it, but my screen still shows nothing. Even pressing the soft reboot doesn't work anymore. Is there any way to get my screen to display something again?

---

### Post by ooglyboo on 2008-01-04
OK, I got it to work. After reading another thread where some people were having the same problem and fixed it by power-cycling, I tried doing the same thing and now everything is working again. :D

---

