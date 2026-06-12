---
title: "Laptop locks up after Dapper Drake upgrade or new install"
date: 2006-08-16
forum: Hardware &amp; Laptops
---

### Post by samvde on 2006-08-16
Hi guys, I am running out of options so I really hope one of you can help me out...

I am running Ubuntu on my laptop, Compaq EVO N610c in a dual boot configuration with WinXP. Although I am familiar with linux in general, I will not pretend to be the big guru either :)

The problem is quite simple: since I upgraded from Breezy to Dapper Drake, my machine locks up regularly but intermittently... This is becoming extremely annoying.

What I tried:

- build the newest kernel using a procedure found on Ubuntu website. Build was succesful, kernel was 2.6.17-5 if I recall well, however, it did not solve the issue.
- upgraded dapper to edgy - this was a big mistake :) However it did run! But the issue was not gone...
- reinstalled Dapper from scratch, since I was planning to migrate the disk anyway (I used to boot it from an external USB disk). So instead of just migrating the disk I reinstalled, and in the process used IDE hda instead of USB sda (which I am working on now). Works great, but it still locks up.

I checked syslog, but it has no entries prior to the reboot.

I can not define the ciscumstances which cause the lock up. There is some internet traffic, but I once had the issue only logged on to the system (Gnome) with a terminal window open.

I installed Ubuntu server 6.06 and used aptitude to install X windows/Gnome/apps from the www. So should have latest pkgs as well.

If there is anybody out there who can help me or point to another log I can use to determine what causes this, this would be highly appreciated.

And BTW, the XP instance never locks up, and the x86 memtest ran for several hours without an issue. I don suspect my hardware - for now.


Rgds
Sam

---

