---
title: "Ubuntu 9.04 video problem on startup"
date: 2009-06-13
forum: Hardware
---

### Post by ZZCheetahZZ on 2009-06-13
Big problem on my HP Compaq 6715s Laptop.
After installing everything and working around all the hardware recognition problems, the system was finally perfect for regular work, then I rebooted it and all the problems began.
Now when it starts up the ubuntu 9.04 desktop, all I see is little flickering of the whole screen and colorful lines across it.   that's about it!  it freezes that way..  can't see no mouse, nothing.  All I can do is press the OFF switch so the laptop will automatically turn off.
I also tried restarting in the "safe mode" and try to repair graphics or broken packages --  NO JOY there.
:(


Thanks.

---

### Post by ZZCheetahZZ on 2009-06-13
Found it!   

this code helped me recover my system:

when in safe mode command prompt with networking:

CODE:
apt-get remove --purge xorg-driver-fglrx

Thanks to [[COLOR=Black]kannedheat[/COLOR]]("http://ubuntuforums.org/member.php?u=301627") on this fix!  :D

---

