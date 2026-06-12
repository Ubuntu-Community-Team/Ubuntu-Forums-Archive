---
title: "windows xp hangs when entering to standby or shutdown after installing ubuntu"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by ungaro on 2006-10-21
hi,

after having installed ubuntu with grub on the same partition with windows xp, i'm experiencing problems within windows xp when it is entering standby mode. it hangs with "preparing for standby" note and all i can do from there is to reboot. 

It is very annoying when i forgot to save documents and battery runs out, i've lost my work repeatedly since this problem starts to occur. I mostly use windows xp and it is very urgent for me to have this standby problem solved...

any ideas?

thanks,
alp

---

### Post by karthikp on 2006-10-21
This doesn't sound like an Ubuntu problem. I had something very similar happen to me and it was because there was some conflict between my firewall (Zone Alarm) and my anti-virus (McAfee). If I uninstalled either, my comp worked fine. I eventually chose to get rid of the firewall rather than the antivirus...In any case, I go to XP mostly for have a fragfest on Halo, which sadly isn't too often nowadays (I digress :) )

There's a decent amount of documentation on the M$ website on this issue (hanging comp on shutdown/standby). One suggestion that gets thrown around quite often is to disable Fast User Switching and change the login screen back to the classic logon prompt. I don't know how useful it is in solving the problem, but it certainly works faster than the glitzy welcome screen. A good place to start, in any case.

Hope this helps.

---

### Post by ungaro on 2006-10-21
well, actually, it should be a grub related problem, because this problem started exactly after having installed ubuntu, and my computer doesn't even shutdown. it shuts down, but the power is always there, so i have to shut down it from power by pressing power button a long time to complete the shutdown process.

---

### Post by karthikp on 2006-10-21
AFAIK, grub just lets you decide which (bootable) partition to boot from. It doesn't really affect the shutdown process (which should be controlled by the OS that you're using) and certainly not the standby process.

---

### Post by ChevyGuy on 2006-10-21
Ungaro, it's not just you, I have the same problem.  I did a clean install of Ubuntu, Dapper, a few days ago.  Same thing, it looks like XP Pro shuts down, but the power is still on.

---

